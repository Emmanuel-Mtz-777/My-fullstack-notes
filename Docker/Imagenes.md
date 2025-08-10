---
tags:
  - Conceptos
  - Docker
autor: Leviek
---
En [[Docker]] una imagen es un conjunto de instrucciones que permiten crear contenedores, estas son **inmutables**, es decir una vez creadas no se pueden modificar, para modificarlas es necesario volverlas a crear.
Están **_formadas por capas (layers)_**, es decir cada paso de la construcción esta guardado en una capa.
Esto permite reutilizar capas en diferentes imágenes para optimizar  espacio y tiempo de descarga.
Lo anterior se refiere a la cache donde tomamos los elementos que cambia solamente en consideración al momento de volver a crear una imagen.
