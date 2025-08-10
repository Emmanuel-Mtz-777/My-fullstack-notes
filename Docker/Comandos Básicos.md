---
tags:
  - Docker
  - Conceptos
  - "#Comandos"
autor: Leviek
---
[[Docker]]
[[Ciclo de vida Contendores]]
# Comandos de ejecución.
### Docker run
Es el comando de arranque de los contenedores.
```
docker run <imageName>
```
Al usar el comando con una imagen que no tenemos descargada, la imagen se descarga en automático y después se ejecuta.

### Modo detach
El modo detach es el modo de ejecucion en segundo plano de los contenedores, se activa utilizando -d en los comandos.
```
docker run <imageName> -d
```
### Docker Stop
Es el comando para detener los contenedores.
```
docker stop <contenedorName> 
```
Otra forma de hacerlo es la siguiente.
```
docker stop <idContenedor>
```
### Docker rm
Para eliminar contendores se utiliza el siguiente comando:
```
docker rm <nombreContenedor>
```
O de la siguiente forma:
```
docker rm <idContenedor>
```
Es importante decir que es necesario que los contenedores estén detenidos para eliminarlos sin problemas, si se desea eliminar un contenedor en ejecución utilizamos el siguiente comando:
```
docker rm -f <idContenedor>
```
O también con el nombre del contenedor:
```
docker rm -f <nombreContenedor>
```
# Comandos de gestión de contenedores.
### Docker ps
Docker ps es un comando que permite ver a los contenedores en ejecución.
```
docker ps
```
Mientras que de la siguiente forma podemos ver todos los contenedores independientemente si están en ejecución o no.
```
docker ps -a
```
### Docker Logs
Los logs son registros que una app o sistema guarda para mostrar lo que sucede incluye errores, eventos o acciones realizadas, son útiles para saber que pasa o para encontrar errores.
Para ver los logs utilizamos:
```
docker logs <idContenedor>
```
El comando anterior muestra los logs hasta el momento de la ejecución del comando.
Para ver los logs a tiempo real utilizamos:
```
docker logs -d <idContenedor>
```

# Comandos de configuración de contenedores.
Los contenedores se pueden personalizar o algunos necesitan configuraciones extra para funcionar como quisiéramos, incluso para configurarlos después de crear el servicio.
### Asignar Nombres
Docker coloca nombres por defecto a los contenedores, pero nosotros podemos decidir el nombre del contendor dependiendo de nuestras necesidades  gustos.
```
docker run -d --name miContenedor <imageName>
```

### Eliminar contenedores detenidos
Para eliminar contenedores detenidos se utiliza
```
--rm
```

### Mapeo de puertos
Los contenedores tienen sus propios puertos por lo que es necesario mapear esos puertos con el del host para poder visualizar o utilizar contenido que esta dentro del contenedor, se hace añadiendo:
```
 -p <Puerto Host>:<Puerto contenedor> 
```
un ejemplo seria:
```
docker run -p 8080:80 nginx
```

### Mapeo de volúmenes
Los contenedores son efímeros, por lo que al detenerlos o eliminarlos se pierde toda la información que contienen. Para conservar datos de forma persistente, es necesario guardar esa información fuera del contenedor y acceder a ella desde ahí. Esto se conoce como mapeo de volúmenes.
Para hacerlos utilizamos tenemos 2 formas:
- #### **Bind Mount**
Donde se toma una carpeta del host para almacenar toda la data del contendor y se utiliza de la siguiente manera:
```
docker run -v /ruta/en/tu/host:/ruta/en/contenedor imagen
```
- #### **Volumen gestionado por Docker**
Donde creamos un volumen con comandos de Docker y simplemente le indicamos al contendor que va a usar ese volumen como almacenamiento:
```
docker volume create mi_volumen
```
Para crear el volumen y al mapearlo necesitamos seguir el siguiente formato:
```
-v <volumen_o_carpeta_host>:<ruta_dentro_contenedor>
```
Entonces la ejecución del contenedor quedaría de la siguiente manera:
```
docker run -v mi_volumen:/data imagen
```

### Variables de entorno
Las variables de entorno son esos datos que necesita el servicio para funcionar por ejemplo:
	Las bases de datos necesitan usuario, contraseña y la base de datos para funcionar.
Se usan de la siguiente manera:
```
docker run -d --name miContenedor -e NOMBRE_VAR1=valor1 -e NOMBRE_VAR2=valor2 <imageName>

```
Otra forma de utilizar variables de entorno es cargarlas desde un archivo de ese modo si tengo varios servicio o planeo levantar varios servicios con la misma configuración se agiliza el proceso.
```
docker run -d --name miContenedor --env-file ruta/al/archivo.env <imageName>
```

### Ejecutar comandos dentro de contendores
A veces es necesario entrar dentro del contendor para hacer configuraciones la forma de hacerlo seria:
```
docker exec <id o nombre> <comando>
```
Existen diferentes tipos de comandos, por ejemplo:
```
docker excec <id o nombre> ls /<ruta>
```
> Que permite listar los archivos del contenedor.
```
docker exec >id o nombre> /bin/bash
```
> Que abre una terminal que muestra una salida si la hubiera.

Pero estos comandos no son interactivos es decir solo mostraran información de lo que hay hasta el momento de la ejecución del comando.
**Para sesiones interactivas** utilizamos:
```
docker exec -it mi_contenedor <comando>
```
Que nos permite trabajar de una manera mas interactiva con el contenedor.
Dentro del  comando vemos que tenemos "**-it**" esto tiene su razon:
- **-t**: Asigna una terminal pseudo-tty, lo que muestra una salida mas amigable.
- **-i**: Mantiene la entrada estandar abierta, permitiendo que podamos escribir dentro del contenedor
Por eso normalmente se utilizan juntos.

Un ejemplo para abrir terminales que nos permitan ejecutar comandos y no ver solo salidas utilizamos:
```
docker exec -it <id o nombre> /bin/bash

docker exec -it mi_contenedor sh
```
