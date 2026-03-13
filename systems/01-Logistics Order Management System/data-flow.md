# Data Flow — Logistics Order Management System

## Order Creation Flow

1 Cliente envía request para crear orden.
2 Orders Service valida datos.
3 Orders Service guarda orden en base de datos.
4 Orders Service publica evento OrderCreated en NATS.

Event:

OrderCreated
{
  order_id
  amount
  customer_id
}

---

## Payment Flow

1 Cliente registra pago.
2 Payments Service valida pago.
3 Payment se guarda en base de datos.
4 Payments Service publica evento PaymentRegistered.

---

## Payment Confirmation Flow

1 Payment Service confirma pago.
2 Se actualiza estado de la orden.
3 Se publica evento PaymentConfirmed.

---

## Notification Flow

1 Notification Service escucha PaymentConfirmed.
2 Se envía notificación al usuario.

---

## Retry Strategy

Si un servicio falla al procesar un evento:

- Retry automático
- Backoff exponencial

Si el mensaje falla repetidamente:

- Enviar a Dead Letter Queue.

---

## Idempotency Strategy

Para evitar procesamiento duplicado:

- Identificador único de evento
- Registro de eventos procesados
- Verificación antes de ejecutar operación.