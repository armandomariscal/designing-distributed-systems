# Designing Distributed Systems

Repositorio de práctica continua para aprender **System Design, arquitectura de software y sistemas distribuidos**.

El objetivo es desarrollar la capacidad de **pensar como arquitecto de software**, diseñando sistemas escalables, resilientes y desacoplados mediante ejercicios prácticos.

Cada ejercicio documenta el diseño de un sistema utilizando:

- análisis de requerimientos
- arquitectura de alto nivel
- flujos de datos
- decisiones técnicas
- trade-offs

El enfoque principal está en arquitectura de **microservicios y sistemas basados en eventos**.

---

# Objetivos del repositorio

- Practicar **System Design** de forma constante.
- Desarrollar pensamiento de **arquitectura de software**.
- Documentar decisiones técnicas.
- Analizar escalabilidad, resiliencia y consistencia.
- Construir un portafolio público de arquitectura de sistemas.

---

# Estructura del repositorio

```text
designing-distributed-systems
│
├── systems
│ ├── 01-logistics-order-management-system
│ │ ├── requirements.md
│ │ ├── architecture.md
│ │ └── data-flow.md
│ │
│ └── ...
│
├── notes
│ ├── consistency-models.md
│ ├── event-driven-architecture.md
│ └── retries-and-backoff.md
│
├── templates
│ └── system-design-template.md
│
└── README.md
```

---

# Systems

Cada carpeta dentro de `systems` representa el diseño de un sistema completo.

Cada sistema incluye:

### requirements.md
Definición del problema y requerimientos funcionales y no funcionales.

### architecture.md
Descripción de la arquitectura, microservicios, comunicación entre servicios y decisiones técnicas.

### data-flow.md
Flujos de eventos y datos dentro del sistema.

---

# Notes

La carpeta `notes` contiene conceptos generales de arquitectura utilizados en diferentes diseños de sistemas.

Ejemplos:

- modelos de consistencia
- arquitectura orientada a eventos
- estrategias de retry y resiliencia

Estos documentos sirven como referencia para los diferentes ejercicios.

---

# Tecnologías utilizadas en los diseños

Los ejercicios de arquitectura están orientados a tecnologías modernas usadas en sistemas distribuidos:

- TypeScript
- NestJS
- Microservicios
- NATS
- Docker
- Linux
- PostgreSQL

---

# Metodología de práctica

Este repositorio se actualiza regularmente con nuevos ejercicios de diseño de sistemas.

Cada ejercicio sigue el proceso:

1. Definir el problema.
2. Analizar requerimientos.
3. Diseñar arquitectura de alto nivel.
4. Definir comunicación entre servicios.
5. Analizar consistencia y resiliencia.
6. Documentar decisiones técnicas y trade-offs.

---

# Áreas de aprendizaje

Los ejercicios cubren temas importantes de **arquitectura de sistemas** dentro de:

- System Design
- Microservices Architecture
- Event Driven Systems
- Distributed Systems
- Scalability
- Fault Tolerance
- Data Consistency
- Observability

---

# Sistemas planeados

Algunos sistemas que se diseñarán en este repositorio:

- Logistics Order Management System
- URL Shortener
- File Processing Pipeline
- Notification Service
- Metrics and Monitoring System
- POS system
- Realtime notifications
- Basic ERP system
- Payment Processing System
- CRM system
- Email service
- Log aggregation system
- Search engine
- Job queue system
- Distributed cache
- Recommendation system
- Rate limiter
- Distributed file storage

---

# Propósito

Este repositorio funciona como:

- laboratorio de arquitectura
- portafolio técnico
- material de estudio para diseño de sistemas
- práctica para entrevistas técnicas de **System Design**

---

# Licencia

MIT
