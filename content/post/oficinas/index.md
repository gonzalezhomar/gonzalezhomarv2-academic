---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Oficinas de Atención al Contribuyente"
subtitle: "Mapeando... otra vez"
summary: "Mapeando... otra vez"
authors: 
- admin
tags: 
- Python
- Maps
- WebScrapping
- Blog
categories: [Blog]
# Date published
categories: []
date: 2021-05-25T17:06:51-05:00
lastmod: 2021-05-25T17:06:51-05:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
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

A través de este pequeño proyecto quise poner en práctica la herramienta de geolocalización de Google Sheets, por lo que repetí unos cuantos mapas. En esta ocasión, mi objetivo puntear en un mapa las [oficinas de atención al contribuyente](https://finanzas.guanajuato.gob.mx/c_oficinas/index.php) que hay en el Estado. La diferencia con mi [anterior mapa](https://gonzalezhomar.netlify.app/post/mi-primer-mapa/) es que en esta ocasión la información esta disponible en excel, pero no tiene la información georeferenciada, por lo que utilicé el complemento de Google Sheets [Geocode](https://finanzas.guanajuato.gob.mx/c_oficinas/index.php).

Con las anteriores herramientas, generé los siguientes mapas:

### Puntos

<iframe
    src='./static/oficinas_puntos.html'
    width='100%'
    height='500px'
    style='border:none;'>
</iframe>

### Cluster de Puntos

<iframe
    src='./static/oficinas_agrupadas.html'
    width='100%'
    height='500px'
    style='border:none;'>
</iframe>

### Nota

El proceso de Geocode no resultó ser muy preciso: corregí los puntos que no detectó, pero hay algunos puntos mal ubicados.