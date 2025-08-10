---
tags:
  - Comandos
  - Conceptos
  - Docker
autor: Leviek
---
Cuando hablamos de **políticas de reinicio** en [[Docker]], nos referimos a cómo se comportará un contenedor ante situaciones que provoquen su detención, ya sea por errores lógicos, fallos eléctricos, fallos de ejecución u otras causas.
**Estas políticas definen si docker intenta reiniciar el contendor o no y en que condiciones.**
Tenemos 4 politicas:
- **no**: No reinicia el contenedor si se detiene o falla; es la opción por defecto.
- **always**: Siempre reiniciará el contenedor, incluso si lo detienes manualmente.
- **unless-stopped**: Reinicia el contenedor siempre, **a menos que lo hayas detenido manualmente**; si tú detienes el contenedor, no se reiniciará automáticamente hasta que lo inicies otra vez.
- **on-failure:n**  : Reinicia el contenedor solo si falla (termina con código distinto de 0). Opcionalmente puedes limitar el número máximo de intentos de reinicio.
La forma de utilizarlas seria la siguiente:

```
docker run --restart <politica> imagen
``` 
 Con cada una seria de la siguiente manera:
```
docker run --restart no nombre_imagen

docker run --restart always nombre_imagen

docker run --restart unless-stopped nombre_imagen

docker run --restart on-failure:5 nombre_imagen
```