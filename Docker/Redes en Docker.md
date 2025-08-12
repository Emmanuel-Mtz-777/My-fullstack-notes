---
tags:
  - Docker
  - Conceptos
autor: Leviek
---
En [[Docker]], las **redes** son un mecanismo que permite la comunicación entre contenedores, o entre contenedores y el mundo exterior, de forma controlada y segura.

Las redes Docker aíslan los contenedores en diferentes segmentos de red, controlan cómo se conectan entre sí y pueden definir reglas de acceso y comunicación.

Permiten:
- **Aislamiento:** Docker permite aislar servicios y contenedores para que solo aquellos que estén relacionados o conectados a una misma red puedan comunicarse entre sí, evitando que contenedores no relacionados tengan acceso o interacción, lo que mejora la seguridad y organización.
- **Conexión:** Docker permite configurar qué contenedores pueden comunicarse entre sí mediante redes específicas, dándote control para permitir o restringir la comunicación entre servicios.
- **Control:** En Docker se pueden gestionar las redes de manera granular, asignando contendores a redes especificas.

## Tipos de redes.
Dentro de las redes en docker tenemos 5 tipos:
- **Bridge**: Tipo de red predeterminada, permite que los contenedores dentro de una misma red se comuniquen entre sí aislándolos del resto del sistema y otras redes.

- **Host**: El contenedor comparte la misma red que el host, eliminando el aislamiento y permitiendo que el contenedor tenga acceso a los recursos del sistema

- **None**: Aísla completamente el contenedor ya que no tiene acceso a ninguna red.

- **Overlay**: _Se utiliza en sistemas distribuidos_ permite comunicar contenedores que están en diferentes host como si estuvieran en la misma red

- **Macvlan**: Asigna una dirección Mac al contenedor permitiendo comportarse como otro dispositivo en la red host
