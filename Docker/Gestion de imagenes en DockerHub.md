---
tags:
  - Comandos
  - Conceptos
  - Docker
autor: Leviek
---
# Commit, save, load, tag y push.

## Commit
A partir de un contenedor, podemos guardar su estado mediante un _snapshot_. Este snapshot captura la imagen base junto con todas las modificaciones realizadas en el sistema de archivos (file system). Además, guarda el estado de la memoria y los metadatos del contenedor, permitiendo así restaurar o replicar el contenedor exactamente en el mismo punto en que se tomó el snapshot.
```
docker commit [OPTIONS] CONTAINER_ID_OR_NAME IMAGE_NAME[:TAG]
```
Un ejemplo seria:
```
docker commit my_container my_image:latest
```

## Save y Load
- **Save**: Sirve para guardar una imagen de Docker en un archivo `.tar`. Esto es útil para exportar la imagen y moverla o respaldarla fuera del entorno Docker, por ejemplo, para compartirla o transferirla a otra máquina.
```
docker save -o imagen_backup.tar mi_imagen:latest
```
- **load**: Sirve para cargar una imagen Docker desde un archivo `.tar` que fue guardado previamente con `docker save`. Así puedes importar esa imagen a tu entorno Docker sin necesidad de descargarla de un repositorio.
```
docker load -i imagen_backup.tar
```

## Tag
tag se utiliza para cambiar el nombre o versión de la imagen.
```
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```
donde  `SOURCE_IMAGE[:TAG]`: es la imagen que ya tenemos y `TARGET_IMAGE[:TAG]`: es el nuevo nombre y etiqueta.

## Push
Se usa para subir una imagen Docker desde tu máquina local a un repositorio remoto, como Docker Hub. Así, otras personas o tus otros equipos pueden descargar y usar esa imagen.
```
docker push mi_usuario/mi_app:v1
```

[[Imagenes]]
[[Dockerfile]]
