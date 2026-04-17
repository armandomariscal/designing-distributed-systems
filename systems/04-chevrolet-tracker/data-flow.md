# Data Flow & Communication: Chevrolet Tracker

## Communication Channels
- **Integración Externa:** El sistema realiza peticiones seguras a YouTrack para extraer el historial de transiciones de los tickets.
- **Internal Flow (Nx Libraries):** * libs/api-interfaces: Define los contratos de datos (DTOs).
    - libs/core-logic: Procesa el cálculo de productividad.
    - libs/data-access: Maneja las transacciones de Prisma.

## Event Flow (Ejemplo: Registro de Logros)
        
- **Trigger:** El sistema detecta un cambio de estado a "Done" en YouTrack o se ejecuta una sincronización manual.
- **Extraction:** El servicio de integración mapea los campos de YouTrack (estimación vs. tiempo real).
- **Processing:** La capa de dominio evalúa la dificultad y asigna el peso correspondiente al "Activity Tracker".
- **Persistence:** Prisma almacena la entrada en la base de datos, vinculando el ID del ticket con la métrica de tiempo calculada.
- **Visualization:** El frontend consume el endpoint de agregados para actualizar el gráfico de barras y el contador de "medallas" de productividad.