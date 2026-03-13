# Architecture — Logistics Order Management System

## Architectural Style

Microservices architecture usando comunicación por eventos mediante NATS.

Principios:

- Servicios desacoplados
- Comunicación asíncrona
- Escalabilidad horizontal
- Tolerancia a fallos

---

## Microservices

### Orders Service
Responsabilidades:

- Crear órdenes
- Cambiar estatus
- Persistir órdenes
- Publicar eventos

Eventos emitidos:

OrderCreated  
OrderStatusChanged

---

### Payments Service

Responsabilidades:

- Registrar pagos
- Validar pagos
- Confirmar pagos

Eventos emitidos:

PaymentRegistered  
PaymentConfirmed

---

### Notification Service

Responsabilidades:

- Enviar notificaciones
- Escuchar eventos de pagos confirmados

Eventos escuchados:

PaymentConfirmed

---

## Infrastructure Components

Message Broker  
NATS para comunicación entre microservicios.

Containerization  
Docker para despliegue de servicios.

Orchestration  
Docker Compose para desarrollo local.

Database  
Cada microservicio posee su propia base de datos.

PostgreSQL.

---

## High Level Architecture

Client  
→ API Gateway  
→ Orders Service  
→ Database

Orders Service  
→ NATS

Payments Service  
← NATS  
→ Database

Notification Service  
← NATS

---

## Consistency Model

Consistencia eventual entre servicios.

Cada microservicio mantiene su propia base de datos para evitar acoplamiento fuerte.

Los cambios se propagan mediante eventos publicados en NATS.

---

## Technical Decisions

NestJS  
Elegido por su arquitectura modular y soporte fuerte para microservicios.

NATS  
Broker ligero con alto throughput ideal para eventos.

Docker  
Permite reproducibilidad de entornos.

SQL  
Garantiza integridad transaccional para órdenes y pagos.