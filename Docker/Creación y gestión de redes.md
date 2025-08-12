---
tags:
  - Comandos
  - Docker
  - Scripts
autor: Leviek
---
Los siguientes son algunos de los comandos relacionados a las [[Redes en Docker]]
## Crear redes.
```
docker network create <nombre_red>
```

## Crear un tipo de red especifica
```
docker network create --driver bridge mi_red_bridge

docker network create --driver host mi_red_host

docker network create --driver none mi_red_none

docker swarm init
docker network create --driver overlay mi_red_overlay

docker network create -d macvlan \
  --subnet=192.168.1.0/24 \
  --gateway=192.168.1.1 \
  -o parent=eth0 mi_red_macvlan
```

## Ver las redes creadas
```
docker network ls
```

## Asignar redes a un contenedor
```
docker run --network <red> imagen
```

## Asignar red a contenedor en ejecución
```
docker network connect <red> <nombre_contenedor>
```

## Eliminar red
```
docker network rm <nombre_red>
```

# Buenas practicas
- **Segregación**
> Mantener aplicaciones independientes en redes distintas.
- **Inspección**
> Es necesario inspeccionar las redes para verificar la configuración
```
docker network inspect <red>
```
- **Limpieza**
> Eliminar las redes no utilizadas con:
```
docker network prune
```

# Beneficios
Nos permiten:
- Crear arquitecturas seguras y eficientes
- Aislar servicios para evitar interferencias o accesos no deseados
- Conectar servicios relacionados
- Configurar ambientes distribuidos o microservicios

**_Las redes host solo se usan si es realmente necesario ya que exponen el contenedor al exterior_**
