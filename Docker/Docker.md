---
tags:
  - "#Docker"
  - "#Conceptos"
  - "#Deploy"
autor: Leviek
---
Docker se ha creado originalmente para transportar software empaquetado en contenedores de una maquina a otra o de un servidor a otro de forma estandarizada.
Lo logra utilizando tecnología de virtualización a nivel de SO para crear entornos ligeros y portables, haciendo que cada contenedor ejecutado en una maquina comparta kernel pero se ejecuten de forma independiente.
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