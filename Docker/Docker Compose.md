---
tags:
  - Docker
  - Conceptos
autor: Leviek
---
Docker compose es una herramienta que facilita la gestión de contendores o de aplicaciones que utilizan múltiples contenedores.
Docker compose permite definir y ejecutar aplicaciones con múltiples contendores utilizando un archivo YAML.
Este archivo centraliza la configuración de los servicios ([[Redes en Docker]], [[Imagenes]], [[Volumenes]]) simplificando el despliegue y administración de las apps

## Permite

- **Definir múltiples servicios**
> Cada servicio representa un contenedor por lo que podemos definir en estos las imágenes, puertos, red, variables de entorno, configuraciones directamente en un archivo.

- **Utilizar imágenes y [[Dockerfile]]**
> Nos permite usar imágenes propias o utilizar imágenes publicas en la red.

- **Ejecución en segundo plano**
> Al igual que los contendores podemos ejecutarlo en segundo plano y añadir políticas de reinicio