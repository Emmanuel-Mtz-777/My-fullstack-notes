---
tags:
  - Docker
  - Comandos
  - Conceptos
autor: Leviek
---
## ENTRYPOINT y CMD

Cuando hacemos los [[Dockerfile]] podemos utilizar diferentes opciones como ENTRYPOINT o CMD, pero cada uno de estos tiene un uso diferente.
Los entrypoint y cmd son instrucciones de comando donde el entrypoint no cambia pero el cmd puede ser modificado desde la ejecución, por ejemplo:
```
docker run my-app
```
En este build de un [[Dockerfile]] supongamos que cmd ejecuta un archivo, pero si hacemos:
```
docker run my-app python another.py
```
Aquí cambiamos el CMD ya que estamos sobrescribiendo la instrucción dentro del dockerfile ya que mandamos el comando desde el [[DockerBuild]].

## ARG
Los argumentos nos permiten declarar variables en los [[Dockerfile]] y estas al igual que el CMD también pueden ser modificadas a la hora de la ejecución.
En el dockerfile:
```
ARG variable=x
```
Y en el build podríamos hacer:
```
docker build --build-arg variable=y -t <tag> .
```

## Variables de entorno
En un [[Dockerfile]] las utilizamos para configurar el comportamiento del contenedor, utilizamos ENV para definirlas y también podemos sobrescribirlas.
En el dockerfile:
```
ENV PORT=3000
```
En la construcción del contenedor:
```
docker run -e PORT=4000 nginx
```
Lo útil de estas es que nos permiten ver diferentes comportamientos sin crear diferentes imágenes.

**_En las variables de entorno podemos definir cosas como usuarios y contraseñas de la bd, entre otras._**
