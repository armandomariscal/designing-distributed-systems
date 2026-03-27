# Requirements: SGI - UE

## Context
Sistema de Gestión Integrada diseñado para cumplir con normativas administrativas de la Unión Europea. El sistema debe centralizar auditorías y procesos legales en un entorno controlado y reproducible.

## Functional Requirements (FR)
* **FR-01: Identidad Visual:** El sistema debe presentar una landing page con color corporativo #1A237E y simbología de la UE.
* **FR-02: Gestión de Entidades:** CRUD completo para proyectos, usuarios y registros administrativos.
* **FR-03: Tareas Asíncronas:** Capacidad de disparar procesos de larga duración (reportes) sin bloquear la navegación.
* **FR-04: Persistencia:** Almacenamiento seguro de estados de tareas y auditorías.

## Non-Functional Requirements (NFR)
* **NFR-01: Disponibilidad:** Garantizar que las tareas en cola no se pierdan ante reinicios (Persistence).
* **NFR-02: Portabilidad:** Despliegue agnóstico al SO mediante Docker "Entorno de referencia: Linux (Probado en Fedora/RHEL con SELinux enabled)".
* **NFR-03: Compatibilidad:** Soporte estricto para Python 2.7 y Django 1.11 (Stack Legacy).
* **NFR-04: Seguridad:** Aislamiento de credenciales mediante variables de entorno (.env).