---
tags:
  - Comandos
  - Docker
autor: Leviek
---
En docker las [[Imagenes]] las podemos crear nosotros mismos o descargarlas y utilizarlas para nuestros contenedores por lo que es muy útil saber gestionar estas.
## Descargar una imagen
>Para descargar una imagen en el host desde algún repositorio online (normalmente Dockerhub) utilizamos:
```
docker pull <nombre de la imagen>
```
## Listar imágenes
>Dentro de nuestro equipo podemos tener diferentes imágenes o diferentes versiones de una imagen por lo que es necesario saber cual utilizar al crear un contenedor para obtener un listado de las imágenes dentro del host usamos:
```
docker images
```
## Obtener layers
>Para visualizar las capas que forman la imagen incluyendo comandos para construirla y tamaño utilizamos:
```
docker history <nombre o id de la imagen>
```
## Eliminar imágenes
>Tenemos 2 opciones para eliminar imagenes dentro de nuestro host las cuales serian:
>-**Eliminar una imagen especifica**:
```
docker rmi <nomnbre o id de la imagen>
```
>-**Eliminar las imágenes no asociadas a contenedores**:
```
docker image prune
```
>Este ultimo pedirá una confirmación para no verla podemos añadir un -f al comando
## Buscar imágenes
Para buscar una imagen en DockerHub utilizamos:
```
docker search <nombre imagen>:<version>
```
La versión es un parámetro opcional pero es recomendado ponerla ya que algunos trabajos necesitan versiones especificas.

