---
tags:
  - Conceptos
  - Docker
  - Comandos
autor: Leviek
---
Los contenedores son efímeros, es decir, tienen una duración corta y están diseñados para ser creados y destruidos fácilmente. Sin embargo, en muchos casos es necesario que los datos persistan más allá de la vida útil de un contenedor, para que no se pierdan cuando este se elimina o reinicia.

Para lograr esta persistencia, se utilizan volúmenes, que permiten almacenar datos fuera del ciclo de vida del contenedor. Sin volúmenes, tendríamos que crear contenedores nuevos constantemente y además establecer mecanismos complejos para que se comuniquen entre sí y compartan información, lo cual es poco eficiente y difícil de mantener.

# Contenedores y volúmenes
**Los volúmenes en [[Docker]]** son archivos o directorios almacenados fuera del sistema de archivos interno del contenedor. Se montan dentro de éste para que pueda acceder y manipular su contenido. Esto permite **persistir datos** incluso si el contenedor se detiene o se elimina, evitando la pérdida de información.

## Comandos de volúmenes
- ### Crear un volumen
```
docker volume create <nombre_volumen>
```
- ### Listar volúmenes existentes
```
docker volume ls
```
- ### Inspeccionar un volumen
```
docker volume inspect <nombre_volumen>
```
- ### Montar un volumen
Para montar volumenes en un contendor se utilizan los parametros "-v" o "--mount" al ejecutar el contenedor.
```
docker run -d \
  --name mi_contenedor \
  -v mi_volumen:/ruta/en/contenedor \
  nginx
```

```
docker run -d \
  --name mi_contenedor \
  --mount source=mi_volumen,target=/ruta/en/contenedor \
  nginx
```
- ### Eliminar volúmenes
```
docker volume rm <nombre_volumen>
```
O eliminar todos los volúmenes no usados:
```
docker volume prune
```
- ### Montar directorios en el host del contenedor
```
docker run -it -v <ruta_host>:<ruta_contenedor> <imagen>
```
- ### Copiar archivos
Podemos copiar directorios del host al contendor y viceversa se utiliza el siguiente formato:
```
docker cp <origen> <destino>
```
Origen y destino pueden ser rutas del contendor o del host, para indicar ruta del contenedor hacemos:
```
<contenedor>:/ruta/en/contenedor
```
El ejemplo seria:
```
docker cp /ruta/en/host/archivo.txt mi_contenedor:/ruta/en/contenedor/

docker cp mi_contenedor:/ruta/en/contenedor/archivo.txt /ruta/en/host/
```
Aunque este proceso es mas simple utilizando docker desktop.