# Architecture Overview: Personal Brand & Portfolio Hub

## Components
- **Central Hub (GitHub Profile):** Este repositorio actúa como el orquestador de identidad, vinculando los 7 temas de interés en desarrollo (QA, System Design, Frontend, Backend, Core, Product, Cloud).
- **Automation Layer (GitHub Actions):** Flujos de trabajo encargados de actualizar dinámicamente las estadísticas de commits, lenguajes y "streaks".
- **External Integration (Vercel/Heroku APIs):** Consumo de servicios externos para la generación de tarjetas de métricas y visualización de actividad en tiempo real.
- **Project Catalog:** Estructura de navegación que conecta los micro-servicios (repositorios individuales) con el perfil principal.

## Trade-offs
- **Curación Manual vs. Automatización:** Se prefiere una actualización manual detallada de la tabla de proyectos para garantizar que la narrativa de "Modern JS Engineer" sea coherente, aunque las estadísticas de actividad sean automáticas.
- **Estandarización de Documentación:** Se sacrifica la rapidez de creación de repositorios a cambio de una estructura rígida de 3 archivos (Architecture, Data Flow, Requirements) para demostrar rigor profesional en System Design.