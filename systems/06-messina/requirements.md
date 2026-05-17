# Requirements: MESsina

## Context

MESsina se diseña para solucionar los problemas críticos de visibilidad y control en plantas de manufactura, donde la pérdida de trazabilidad de los materiales y la falta de datos en tiempo real sobre el estado de la maquinaria provocan cuellos de botella e ineficiencias operativas.

## Functional Requirements (FR)

### Core Workflows & Production

- **FR-01: Gestión de Órdenes de Producción:** El sistema debe rastrear el ciclo de vida completo de una orden (Created, Scheduled, In Progress, Paused, Completed, Cancelled).
- **FR-02: Control de Transición de Estaciones:** Controlar las transiciones de estado de las estaciones físicas de trabajo (ej: Configuración, Producción, Paro por Mantenimiento, Espera de Material).

### Traceability & Quality

- **FR-03: Trazabilidad de Inventario:** Registrar la entrada, consumo y movimiento interno de materias primas vinculándolas directamente a lotes y órdenes de producción específicas.
- **FR-04: Control de Calidad y Desperdicio:** Permitir el registro de incidencias, piezas defectuosas (scrap) y flujos de retrabajo asociados a una estación o lote.

### Metrics & Operations

- **FR-05: Logs de Auditoría Inmutables:** Generar una traza inauditable e histórica de cada evento operativo crucial realizado por usuarios o automatizaciones.
- **FR-06: Reportes de Productividad:** Calcular métricas de manufactura básicas (Rendimiento de producción, tiempos muertos y disponibilidad).

## Non-Functional Requirements (NFR)

- **NFR-01: Modularidad Rigurosa:** El código de la aplicación backend debe estructurarse de tal manera que las dependencias entre aplicaciones (`apps/`) estén claramente delimitadas para permitir una migración limpia a microservicios en el futuro si fuera requerido.
- **NFR-02: Garantía de Transaccionalidad:** Las operaciones críticas que involucren inventario y cambios de estado deben ejecutarse bajo transacciones atómicas de base de datos para evitar estados inconsistentes (Race conditions).
- **NFR-03: Desacoplamiento de Tareas Pesadas:** Cualquier proceso de agregación de datos o reportes históricos que tome más de 200ms debe ser procesado de manera asíncrona mediante trabajadores Celery.
- **NFR-04: Huella de Infraestructura Ligera:** El diseño técnico debe ser óptimo para correr eficientemente en hardware limitado (entornos locales u on-premises de plantas industriales) mediante el uso de contenedores Docker optimizados.
