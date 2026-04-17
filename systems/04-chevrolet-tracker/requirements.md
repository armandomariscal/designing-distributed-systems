# Requirements: Chevrolet Tracker

## Context
Este sistema actúa como una capa de inteligencia y auditoría de datos sobre el flujo de trabajo en YouTrack. Su objetivo es centralizar, procesar y visualizar el rendimiento técnico individual mediante el análisis de tickets, tiempos y complejidad.

## Functional Requirements (FR)
* **FR-01: Ingesta de Datos YouTrack:** Sincronización de tarjetas completadas a través de la API de YouTrack (ID, título, descripción, tiempos).
* **FR-02: Categorización de Dificultad:** Clasificación de tareas basada en puntos de historia o metadatos técnicos para normalizar el esfuerzo invertido.
* **FR-03: Dashboard de Productividad:** Visualización de métricas clave (Throughput, Cycle Time, Lead Time) mediante indicadores visuales de progreso.
* **FR-04: Reporte de Evidencia:** Generación de reportes detallados que vinculen el tiempo invertido con los entregables técnicos finales.

## Non-Functional Requirements (NFR)
* **NFR-01: Estructura Monorepo:** Gestión de aplicaciones y librerías mediante Nx para asegurar la consistencia del código.
* **NFR-02: Persistencia Robusta:** Uso de Prisma ORM para garantizar la integridad referencial de los logs de actividad.
* **NFR-03: Trazabilidad:** Cada registro de actividad debe ser inmutable para servir como auditoría técnica.
* **NFR-04: Eficiencia de Consulta:** Optimización de queries para el cálculo de agregaciones de tiempo y dificultad.