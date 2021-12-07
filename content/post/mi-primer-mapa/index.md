---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Mi primer mapa"
subtitle: "Puntos de Pago en Guanajuato"
summary: ""
authors: 
- admin
tags: 
- Python
- Maps
- WebScrapping
- Blog
categories: [Blog]
# Date published
date: "2020-01-30T00:00:00Z"

# Date updated
lastmod: "2020-01-30T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Mi primer mapa"
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

---

## Objetivo

A través de este pequeño proyecto quise poner en práctica diferentes herramientas:

### Web Scraping.
No conozco la traducción literal de esta habilidad, pero se refiere a la capidad de tomar datos disponibles en internet, sin que tengan un medio para ser extraídos. Sobre este tema hay opiniones encontradas, pues de un lado están quienes señalan que esto es robo de información, y del otro, que es solo una forma de extraer información que ya se encuentra de manera pública.

Formó parte del segundo grupo, así que decide poner en práctica estos conocimientos y tomar algo de información pública, y hacer algo con ella.

### Mapeo.
Como me gusta la programación, la economía y la visualización de datos, soy de la opinión que una de las mejores gráficas que se pueden lograr es un mapa. En especial si es interactivo, pues permite a quién ve la gráfica, visualizar puntos de interés y llama mucho su atención.

## Resultados

Con lo anterior en mente, me puse a buscar qué cosas tenía a la mano. Como trabajo en la Secretaría de Finanzas, Inversión y Administración del Estado de Guanajuato, me tope con esta página con los [puntos de pago](https://finanzas.guanajuato.gob.mx/c_puntos_pago/index.php) que hay en el Estado.

Me puse a trabajar sobre esa información porque considero que la tabla se ve muy fea y es poco accesible (no tiene botón de descarga). Así que con ello en mente, con algo de programación en Python, extraje los puntos a un base de datos, y cree el siguiente mapa:

<iframe
    src='./static/PuntosdePago.html'
    width='100%'
    height='1000px'
    style='border:none;'>
</iframe>