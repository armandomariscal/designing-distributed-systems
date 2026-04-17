# Architecture Overview: Chevrolet Tracker

## Components
- **Workspace (Nx):** Monorepo configurado para separar la lógica de negocio en librerías compartidas y aplicaciones ejecutables.
- **API Service (Node.js + Prisma):** Backend encargado de la orquestación de datos.
    - **Prisma Client:** Capa de acceso a datos que interactúa con la base de datos de auditoría.
    - **Integrator Layer:** Módulo especializado en el consumo y mapeo de la API externa (YouTrack).
    - **Domain Layer (Core):** Contiene la lógica para el cálculo de "medallas", niveles de dificultad y validación de tiempos.
    - **Shared UI Components:** Librería de componentes visuales (gráficas y barras de progreso) para la representación de logros.

## Trade-offs
- Sobrecarga de Abstracción vs. Rigurosidad: Se utiliza Prisma y una estructura de librerías en Nx para garantizar que los datos de trabajo sean indiscutibles y fáciles de auditar, aunque esto requiera más configuración inicial que un script simple.
- Sincronización Asíncrona: Los datos no se consultan en tiempo real a YouTrack en cada vista; se pre-procesan en la base de datos local para asegurar que la visualización de métricas sea instantánea.