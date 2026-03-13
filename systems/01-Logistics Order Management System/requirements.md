# Requirements — Logistics Order Management System

## Context
Sistema para gestionar órdenes en una empresa logística.  
Debe permitir registrar órdenes, actualizar su estado, registrar pagos y notificar cuando el pago sea confirmado.

Tecnologías objetivo:

- TypeScript
- NestJS
- Microservicios
- NATS
- Docker
- Linux
- PostgreSQL

---

## Functional Requirements

1. Crear órdenes.
2. Cambiar estatus de órdenes.
3. Registrar pagos.
4. Confirmar pago.
5. Notificar eventos cuando una orden se crea.
6. Notificar eventos cuando un pago es confirmado.

---

## Non Functional Requirements

- Arquitectura de microservicios.
- Escalabilidad horizontal.
- Tolerancia a fallos parciales.
- Comunicación asíncrona entre servicios.
- Consistencia eventual entre componentes.
- Observabilidad del sistema.
- Manejo seguro de errores.

---

## Domain Entities

Order
- id
- customer_id
- amount
- status
- created_at

Payment
- id
- order_id
- amount
- status
- created_at

OrderStatus
- CREATED
- PROCESSING
- PAID
- CANCELLED

---

## Key Events

OrderCreated  
OrderStatusChanged  
PaymentRegistered  
PaymentConfirmed