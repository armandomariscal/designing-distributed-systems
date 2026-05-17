# Data Flow & Communication: MESsina

## Communication Channels

- **Síncrono (HTTP / REST):** El cliente interactúa mediante HTMX o llamadas REST directas para operaciones transaccionales inmediatas (ej: iniciar un turno o registrar un defecto de calidad).
- **Asíncrono (Task Queue):** Django delega tareas no críticas para el tiempo de respuesta del usuario a Redis/Celery.
- **Inter-módulo:** Se prioriza la separación por capas; si `quality` necesita validar un lote de `inventory`, invoca un método del servicio público expuesto por el módulo dueño, evitando herencia directa o consultas altamente acopladas.

## Event Flow (Ejemplo: Transición de Estado de Máquina e Impacto en OEE)

```markdown
[Cliente/Máquina] -> (POST /api/stations/1/transition/) -> [Stations Module]
|
(Valida reglas de estado y persiste)
|
v
[Audit Module] <--- (Dispara Tarea Asíncrona Celery) <--- [PostgreSQL Update]
|
v
[Celery Worker] ---> (Calcula métricas de tiempo de actividad) ---> [Reporting Module]
```

1. **Trigger:** Un operador o sensor web registra un cambio de estado en una estación de trabajo (ej: de _Running_ a _Down_ por falla mecánica).
2. **Validation & Change:** El módulo `stations` valida la máquina contra la máquina de estados configurada. Si es válida, abre una transacción en PostgreSQL.
3. **Audit Trail:** El módulo `audit` intercepta la confirmación del cambio (mediante señales o decoradores de servicio) y registra una entrada inmutable de auditoría con la marca de tiempo exacta.
4. **Asynchronous Aggregation:** Se encola una tarea en Celery a través de Redis. El worker procesa la transición en segundo plano para actualizar los indicadores de rendimiento de la planta (OEE - Overall Equipment Effectiveness) en el módulo `reporting`, previniendo que el bloqueo de base de datos impacte la experiencia del operador.
