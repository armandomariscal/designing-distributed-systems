# MESsina

Manufacturing execution platform focused on production workflows, machine orchestration, traceability, and operational visibility.

## Stack

![Python](https://img.shields.io/badge/Python-3.9-3776AB?logo=python)
![Django](https://img.shields.io/badge/Django-3.2-092E20?logo=django)
![DRF](https://img.shields.io/badge/DRF-API-red)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13-4169E1?logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-6-DC382D?logo=redis)
![Celery](https://img.shields.io/badge/Celery-Async-37814A)
![Bulma](https://img.shields.io/badge/Bulma-0.9-00D1B2?logo=bulma)
![Alpine.js](https://img.shields.io/badge/Alpine.js-3-8BC0D0)
![HTMX](https://img.shields.io/badge/HTMX-Progressive_UI-3366CC)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker)
![Architecture](https://img.shields.io/badge/Architecture-Modular_Monolith-8A2BE2)

---

## Overview

MESsina is a manufacturing execution system (MES) inspired by industrial production environments and factory-floor operational workflows.

The project explores software engineering concepts commonly found in production-grade operational systems, including:

- production order lifecycle management
- station state transitions
- inventory traceability
- operational audit trails
- asynchronous workflow processing
- reporting and manufacturing metrics
- modular backend architecture

---

## Tech Stack & Structure

### Backend & Frontend

- **Core:** Python 3.9 / Django 3.2 (Modular Monolith) + Django REST Framework.
- **UI:** HTMX + Alpine.js + Bulma (Renderizado progresivo eficiente sin la complejidad de un SPA).
- **Async & Data:** Redis (Broker/Cache), Celery (Workers asíncronos), PostgreSQL (Persistencia).

### Project Layout

```txt
.
├── apps
│   ├── audit          # Trazabilidad e historial inmutable
│   ├── core           # Abstracciones base y utilerías
│   ├── inventory      # Movimientos de stock y materia prima
│   ├── notifications  # Alertas y eventos de planta
│   ├── production     # Ciclo de vida de Órdenes de Producción
│   ├── quality        # Gestión de scrap, defectos y retrabajo
│   ├── reporting      # Cálculo de métricas (OEE, Rendimiento)
│   ├── stations       # Control de estaciones y maquinaria
│   └── users          # Autenticación y RBAC
```

## Development Focus

Estatus del proyecto: `Privado`

- Arquitectura Modular: Aislamiento de contextos dentro de un único despliegue.

- Integridad Transaccional: Control estricto sobre cambios de estado concurrentes en líneas de producción.

- Procesamiento Asíncrono: Delegación de tareas pesadas (mecanismos de reportes y alertas) fuera del ciclo Request/Response.
