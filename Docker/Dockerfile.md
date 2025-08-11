---
tags:
  - Conceptos
  - Docker
  - "#Scripts"
  - Comandos
autor: Leviek
---
Un dockerfile es un archivo de texto que le dice a [[Docker]] como crear una imagen, es similar a un recetario ya que contiene las instrucciones para la creación de [[Imagenes]]
Estos archivos normalmente contienen las siguientes instrucciones:
- **FROM:** Define la imagen base.
- **WORKDIR:** Establece la dirección de trabajo.
- **COPY:**  Copia archivos del host al contenedor
- **RUN:** Ejecuta comandos durante la construcción de la imagen.
- **Expose:** Expone un puerto para el contenedor
- **CMD:**  Define el comando que se ejecuta al iniciar el contenedor; Este comando puede sobrescribirse así que se usa solo si no se utilizara otro comando.
- **ENTRYPOINT:** Similar a CMD, define el comando que se ejecutara al iniciar el contenedor, pero no se sobrescribe facilmente.

Un ejemplo de un dockerfile seria el siguiente:
```
FROM node:18-alpine
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install --production
COPY . .
EXPOSE 3000
CMD ["node", "index.js"]

```

[[DockerBuild]]