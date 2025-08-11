---
tags:
  - "#Docker"
  - "#Conceptos"
autor: Leviek
---
Docker fue creado originalmente para transportar software empaquetado en contenedores de una máquina a otra, o de un servidor a otro, de forma estandarizada y eficiente. Utiliza tecnología de virtualización a nivel de sistema operativo para crear entornos ligeros y portables, donde cada contenedor comparte el kernel del host pero se ejecuta de forma aislada e independiente.

Además, Docker está desarrollado principalmente en el lenguaje de programación [[Go]], lo que le permite ser rápido, eficiente y multiplataforma. Gracias a esto, Docker facilita la creación, distribución y ejecución de aplicaciones en contenedores que incluyen todas sus dependencias, garantizando consistencia en distintos entornos.
Ejemplo:
	Una máquina linux que ejecuta distintos contenedores comparte kernel con ellos.
Al mismo tiempo los contenedores se empaquetan con todas sus dependencias en un entorno aislado, proporcionando una forma segura y más fácil de empaquetar, distribuir y ejecutar software.  
[[Contenedores vs MV.canvas|Contenedores vs MV]]
## Conceptos Básicos
#### Imágenes.
Las imágenes son el corazón de Docker y los contenedores, son archivos binarios que contienen todo lo necesario para ejecutar un software.
Las imágenes son plantillas las cuales pueden incluir:
- Apps.
- Librerías.
- Configuraciones.
#### Contenedores
Los contenedores son instancias de una imagen, son procesos aislados que pueden ejecutar aplicaciones, tareas que finalizan o servicios que se mantienen en ejecución.

#### Dockerfile
Es un archivo de texto que contiene instrucciones secuenciales los cuales ayudan a construir una imagen personalizada, estas instrucciones contienen desde la imagen base, dependencias, e incluso la forma de ejecución.
#### Docker Hub
Repositorio de imágenes de contenedores donde se pueden almacenar imágenes y compartir imágenes creadas por la comunidad o empresas.


[[Ciclo de vida Contendores]]
[[Comandos Básicos]]