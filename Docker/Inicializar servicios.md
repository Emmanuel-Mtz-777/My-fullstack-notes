---
tags:
  - Comandos
  - Conceptos
  - Docker
autor: Leviek
---
Cuando utilizamos [[Docker Compose]] necesitamos un archivo **_docker-compose.YAML_** como el siguiente:
```
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html

```
En el cual podemos inicializar servicios con el siguiente comando:
```
docker compose up
```
Para una ejecución en segundo plano:
```
docker compose up -d
```
Para archivos que tengan un nombre diferente al convencional usamos:
```
docker compose -f <nombre_archio.YAML> -d
```
Para listar servicios activos usamos:
```
docker compose ps
```
Para listar todos los servicios usamos:
```
docker compose ps -a
```
Para ver logs usamos:
```
docker compose logs
```
Para ver logs en tiempo real usamos:
```
docker compose logs -f
```
Para ejecutar comandos en un servicio usamos:
```
docker compose exec <servicio> <comando>
```
Donde los mas utilizados son **_bash_** y **_sh_**
Para terminar con todos los servicios usamos:
```
docker compose down
```