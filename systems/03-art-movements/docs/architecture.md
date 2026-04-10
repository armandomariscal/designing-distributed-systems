# Architecture Overview: Art Movements System

## Components
- **Frontend (Vue 3 + Vite):** SPA organizada por módulos. Utiliza Tailwind CSS para la interfaz y Vite como bundler.
- **Backend (Node.js + TypeScript):** Implementa Clean Architecture dividida en 3 capas:
    - **Domain:** Entidades puras y reglas de negocio.
    - **Application:** Casos de uso (ej. GetMovements.ts).
    - **Infrastructure:** Adaptadores de entrada (Express/Server) y salida (Persistencia).
- **Containerization:** Dockerización de ambos servicios para paridad entre entornos.

## Trade-offs
- Boilerplate vs. Rapidez: Se ha elegido un exceso de archivos (interfaces, d.ts, carpetas por capa) para ganar mantenibilidad a largo plazo, a costa de una velocidad de desarrollo inicial más lenta.
- Client-side Rendering (CSR): Se utiliza Vue (SPA) por la interactividad, sacrificando un poco de SEO inicial, compensado con una estructura de rutas limpia.