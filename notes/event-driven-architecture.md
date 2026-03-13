# Event Driven Architecture

La arquitectura basada en eventos es un patrón donde los servicios se comunican mediante eventos en lugar de llamadas directas.

Un evento representa algo que ya ocurrió en el sistema.

Ejemplo:

OrderCreated  
PaymentConfirmed  
UserRegistered

---

## Conceptos Principales

Event Producer

Servicio que genera el evento.

Ejemplo:
Orders Service genera OrderCreated.

---

Event Broker

Sistema que transporta eventos entre servicios.

Ejemplos:

- NATS
- Kafka
- RabbitMQ

---

Event Consumer

Servicio que escucha eventos y reacciona a ellos.

Ejemplo:
Notification Service escucha PaymentConfirmed.

---

## Ventajas

Desacoplamiento entre servicios.

Los servicios no necesitan conocer a los consumidores de sus eventos.

Escalabilidad.

Los consumidores pueden escalar independientemente.

Extensibilidad.

Nuevos servicios pueden suscribirse a eventos existentes.

---

## Desventajas

Mayor complejidad operativa.

Dificultad para depurar flujos de eventos.

Consistencia eventual.

---

## Buenas prácticas

Eventos inmutables.

Un evento nunca debe modificarse.

Versionado de eventos.

Permite evolucionar el sistema sin romper consumidores.

Idempotencia.

Los consumidores deben poder procesar eventos duplicados sin efectos secundarios.

---

## Uso típico

- microservicios
- procesamiento de eventos
- sistemas de alta escala
- pipelines de datos