---
tags:
  - Comandos
  - Conceptos
  - Docker
  - "#SistemasDistribuidos"
autor: Leviek
---
**Docker Swarm** es una herramienta integrada en [[Docker]] para la orquestación de contenedores, especialmente diseñada para entornos distribuidos.  
Permite escalar, distribuir y gestionar aplicaciones compuestas por múltiples contenedores a través de varios nodos, facilitando la administración centralizada y mejorando las limitaciones de [[Docker Compose]].

Se puede considerar una alternativa o competidor de Kubernetes, aunque Kubernetes es más complejo y con más funcionalidades avanzadas, mientras que Docker Swarm es más sencillo y está más integrado al ecosistema Docker.

# Activación de los nodos
```
docker swarm init
```
Lo que convierte al equipo en el manager o nodo maestro donde este gestiona la carga, el comando anterior nos dará una respuesta como la siguiente para crear los nodos workers:
```
docker swarm join --token SWMTKN-1-2yyciems72bn9cvxbn9524xvf53vtk14cnx3l7hk14ks53eeza-2s7ou8qrq7n7s4gg79ypt4lap 192.168.65.3:2377
```

## Servicios y stacks
Docker swarm trabaja con servicios y stacks, con los servicios podemos lanzar varias replicas de un contenedor para balancear la carga, mientras que los stacks permiten agrupar varios servicios y lanzarlos con un solo comando.
Esto permite balancear cargas ya que el usuario puede visitar una replica mientras otro visita otra pero ambas componen un solo servicio.
```
docker service create --name mi_servicio --replicas 3 -p 80:80 nginx
```
para listar servicios:
```
docker service ls
```
Para ver los logs del servicio:
```
docker service logs
```

## Ventajas
- **Escalabilidad**
> Permite escalar de forma sencilla , por ejemplo aumentando el numero de replicas de un contenedor:
```
docker service scale mi_nginx=10
```
- **Actualizaciones**
> Nos permite actualizar un servicios sin detenerlos, lo que nos permite actualizar sin perder disponibilidad ya que la actualización ocurre en una o varias replicas y después en las demás.
```
docker service update [opciones] <nombre_servicio>
```
> por ejemplo actualizando una version:
```
docker service update --image nginx:1.21 mi_nginx
```
- **Rollbacks**
> Docker Swarm mantiene un historial de las versiones anteriores de un servicio cuando se realizan actualizaciones.
> Si una actualización causa problemas o no funciona como se esperaba, puedes revertir fácilmente el servicio a la versión anterior usando un comando de rollback.
> Esto permite mantener la disponibilidad y estabilidad del sistema, minimizando el impacto de posibles errores durante las actualizaciones.
```
docker service rollback <nombre_servicio>
```


## Stacks
Los stacks se ejecutan desde los docker-compose.YML
```
docker stack deploy -c docker-compose.yml <nombre_stack>
```
Por ejemplo:
```
docker stack deploy -c docker-compose.yml mi_stack
```
Para detenerlos usamos:
```
docker stack rm <nombre_stack>
```
Lo cual detiene los servicios y los elimina.