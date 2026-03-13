# Retries and Backoff

En sistemas distribuidos los fallos temporales son comunes.

Por ejemplo:

- timeouts
- caídas temporales de red
- servicios sobrecargados

Los mecanismos de retry permiten intentar nuevamente una operación fallida.

---

## Retry

Consiste en reintentar una operación después de que falla.

Ejemplo:

Un servicio intenta publicar un evento y falla por un error temporal de red.

El sistema intenta nuevamente.

---

## Problema de Retry Inmediato

Si muchos servicios reintentan inmediatamente puede ocurrir:

retry storm

Esto puede empeorar la sobrecarga del sistema.

---

## Exponential Backoff

Estrategia donde el tiempo entre intentos aumenta progresivamente.

Ejemplo:

1er intento: inmediato  
2do intento: 100 ms  
3er intento: 500 ms  
4to intento: 2 s  
5to intento: 10 s

Esto reduce presión en el sistema.

---

## Jitter

Se agrega una variación aleatoria al tiempo de espera para evitar que múltiples clientes reintenten al mismo tiempo.

---

## Dead Letter Queue

Si un mensaje falla repetidamente, se envía a una cola especial.

Esto permite:

- análisis manual
- reprocesamiento posterior
- evitar bloqueo del sistema

---

## Idempotency

Las operaciones deben ser idempotentes para soportar retries.

Procesar el mismo evento varias veces debe producir el mismo resultado.

---

## Uso en Sistemas de Eventos

En brokers como NATS o Kafka:

- consumidores pueden reintentar procesamiento
- mensajes fallidos pueden enviarse a dead letter queues
- se aplican estrategias de backoff para evitar saturación