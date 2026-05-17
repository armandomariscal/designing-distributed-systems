# Architecture Overview: MESsina (MES Platform)

## Architectural Pattern: Modular Monolith

Se optó por un **Monolito Modular** en lugar de microservicios para mitigar la complejidad operativa inicial (red, service discovery, latencia distribuida), manteniendo un alto nivel de aislamiento de dominio a través de aplicaciones de Django independientes (`apps/`). Cada módulo encapsula sus propias reglas de negocio y modelos.

## Components

- **Client Layer (Progressive UI):** UI renderizada en el servidor mediante plantillas de Django, potenciada con **HTMX** para intercambios de fragmentos HTML asíncronos y **Alpine.js** para el estado local interactivo en el cliente.
- **Application Server (Django Modular Backend):**
  - **API Gateway / Routing (DRF):** Expone contratos REST para integraciones externas y la interacción de la UI local.
  - **Domain Modules (Apps):** Unidades lógicas aisladas (`production`, `stations`, `inventory`, etc.). La comunicación entre módulos se restringe idealmente a llamadas de servicios públicos o eventos internos para evitar un acoplamiento directo en la base de datos.
- **Asynchronous Processing Engine:**
  - **Celery Workers:** Ejecutan procesos de larga duración (cálculo de métricas complejas, agregaciones de auditoría y reportes OEE).
  - **Redis:** Actúa como el Message Broker de alta velocidad para Celery y capa de almacenamiento en caché de estados críticos de las estaciones.
- **Persistence Layer:**
  - **PostgreSQL:** Base de datos relacional encargada de asegurar la integridad transaccional (ACID), crucial para el control de inventarios y trazabilidad.

## Trade-offs

- **Monolito Modular vs. Microservicios:** Se gana simplicidad en el despliegue, refactorización y transaccionalidad nativa en la base de datos. Sin embargo, requiere una disciplina estricta de desarrollo para evitar que las consultas cruzadas (Join queries) rompan las fronteras de los módulos de Django.
- **Renderizado del Lado del Servidor (HTMX) vs. SPA (React/Vue):** Reduce drásticamente el tiempo de carga inicial y elimina la necesidad de duplicar modelos de datos/validaciones en el frontend. El trade-off es que las transiciones complejas de la interfaz de usuario que dependen 100% de micro-interacciones cliente local se vuelven más complejas de gestionar que en un framework SPA dedicado.
