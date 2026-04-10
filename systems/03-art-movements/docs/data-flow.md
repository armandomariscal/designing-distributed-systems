# Data Flow & Communication: Art Movements

## Communication Channels
- **Sync (REST):** El Frontend (Vue) realiza peticiones HTTP al Backend (Express) a través del puerto configurado.
- **Internal Flow:** * Controller recibe el request.
    - Controller invoca al UseCase.
    - UseCase interactúa con el Domain y solicita datos vía interfaces.

## Event Flow (Ejemplo: Obtener Movimientos)

- **Trigger:** El usuario accede a MovementsListView.vue.
- **Request:** El MovementService.ts en el frontend hace un fetch al backend.
- **Process:** El servidor recibe la petición en MovementController.ts, que ejecuta la lógica en GetMovements.ts.
- **Response:** Se retornan los DTOs (Data Transfer Objects) tipados hacia el frontend para su renderizado.