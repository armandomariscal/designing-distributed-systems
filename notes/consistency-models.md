# Consistency Models

En sistemas distribuidos, la consistencia define cómo y cuándo los cambios en los datos se propagan entre diferentes nodos del sistema.

Los microservicios suelen trabajar con múltiples bases de datos y comunicación asíncrona, por lo que elegir un modelo de consistencia adecuado es una decisión arquitectónica importante.

---

## Strong Consistency

Todos los clientes ven exactamente el mismo estado de los datos en todo momento.

Después de escribir un dato, cualquier lectura posterior devuelve el valor actualizado.

Ventajas:
- Simplicidad mental
- Integridad fuerte

Desventajas:
- Mayor latencia
- Difícil de escalar en sistemas distribuidos

Ejemplo:
Transacciones en bases de datos SQL.

---

## Eventual Consistency

Los cambios se propagan gradualmente entre nodos hasta que todos alcanzan el mismo estado.

Durante un periodo corto puede existir inconsistencia.

Ventajas:
- Alta escalabilidad
- Alta disponibilidad

Desventajas:
- Complejidad en lógica de negocio
- Estados intermedios posibles

Ejemplo:
Sistemas basados en eventos.

---

## Read Your Writes

Un cliente que escribe datos puede leer inmediatamente su propio cambio.

Esto mejora la experiencia de usuario en sistemas eventualmente consistentes.

---

## Monotonic Reads

Una vez que un cliente ve una versión de los datos, nunca verá una versión anterior.

---

## Uso en Microservicios

Los microservicios suelen usar consistencia eventual cuando:

- los servicios tienen bases de datos independientes
- se comunican mediante eventos
- se prioriza disponibilidad y escalabilidad

---

## Trade-offs

Elegir un modelo de consistencia implica balancear:

- latencia
- disponibilidad
- integridad de datos
- complejidad del sistema