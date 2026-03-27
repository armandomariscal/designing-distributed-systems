# Architecture Overview: SGI - UE

## Components
* **Web (Django 1.11):** Servidor de aplicaciones WSGI. Maneja la lógica de negocio y el ORM.
* **Worker (Celery 3.1):** Proceso independiente para ejecución de tareas distribuidas.
* **Broker (RabbitMQ):** Bus de mensajes AMQP que comunica Web y Worker.
* **Database (PostgreSQL 9.6):** Motor relacional para persistencia de datos y estados de Celery.

## Deployment Strategy
* **Containerization:** Uso de Docker Compose para orquestar los 4 servicios.
* **Entrypoint Logic:** Scripts de bash para control de flujo y healthchecks de base de datos.
* **Storage:** Volúmenes bindeados con permisos específicos (`sudo chown -R $USER:$USER .`).

## Trade-offs
* **Legacy Stack:** Se asume el riesgo técnico de Python 2.7 para mantener compatibilidad con librerías críticas de la UE.
* **Async Complexity:** Se introduce RabbitMQ para evitar Timeouts en el servidor web durante procesos pesados.