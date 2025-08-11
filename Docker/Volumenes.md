---
tags:
  - Conceptos
  - Docker
  - Comandos
autor: Leviek
---
Los contenedores son efímeros, es decir, tienen una duración corta y están diseñados para ser creados y destruidos fácilmente. Sin embargo, en muchos casos es necesario que los datos persistan más allá de la vida útil de un contenedor, para que no se pierdan cuando este se elimina o reinicia.

Para lograr esta persistencia, se utilizan volúmenes, que permiten almacenar datos fuera del ciclo de vida del contenedor. Sin volúmenes, tendríamos que crear contenedores nuevos constantemente y además establecer mecanismos complejos para que se comuniquen entre sí y compartan información, lo cual es poco eficiente y difícil de mantener.

# Contenedores y volumenes
