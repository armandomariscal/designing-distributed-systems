# Data Flow & Communication: SGI - UE

## Communication Channels
1. **Request/Response (Sync):** Usuario <-> Django via HTTP Port 8000.
2. **Task Queue (Async):** Django -> RabbitMQ (Exchange) -> Celery Worker.
3. **Database I/O:** Todos los servicios <-> PostgreSQL vía Port 5432.

## Event Flow (Task Execution)
1. El usuario interactúa con la UI (Landing/Admin).
2. Django genera un `task_id` y lo envía al Broker.
3. El Broker entrega la tarea al primer Worker disponible.
4. El Worker ejecuta la lógica y actualiza el `status` en la DB.
5. Django consulta la DB para mostrar el progreso al usuario.

## Initial Data Schema
* **User Entity:** Control de acceso y perfiles.
* **Project Entity:** Datos maestros del ERP.
* **Task Results:** Almacenamiento de metadatos de procesos asíncronos.