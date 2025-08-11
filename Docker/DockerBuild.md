---
tags:
  - Docker
  - Comandos
  - Conceptos
autor: Leviek
---
Después de la creación del [[Dockerfile]] usamos el docker build para construir la imagen utilizando el siguiente comando:
```
docker build -t <nombre> .
```
donde "-t nombre" crea un tag que le asigna el nombre a la imagen y nos permite reconocerla fácilmente, mientras que el "." crea el contexto de construcción (el directorio actual y los archivos a copiar).
Otra forma de hacerlo seria:
```
docker build .
```

[[Docker]] tomara las instrucciones del dockerfile y las ejecutara para crear las distintas layers de la imagen.
Esto permite cachear imágenes, es decir, sin una capa no ha cambiado se reutilizara con el fin de agilizar las construcciones de las imágenes.

Entonces en vez de eliminar y reconstruir una imagen desde 0 podemos tomar una imagen inicial y tomar los elementos que no han cambiado para crear una imagen diferente ahorrando tiempo y recursos, por eso es importante etiquetar las imágenes para reconocerlas fácilmente.

Lo importante es que **_la cache aplica tanto para la modificación del dockerfile como de los archivos copiados._**
