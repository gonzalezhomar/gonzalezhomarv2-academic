---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Elecciones 2021 en Guanajuato, Parte 1: Diputados Federales"
subtitle: "Un pequeño análisis geográfico de las elecciones a Diputados Federales en Guanajuato"
summary: "Un pequeño análisis geográfico de las elecciones a Diputados Federales en Guanajuato"
authors: [admin]
tags: [Python, Folium, Elecciones 2021, Guanajuato, Mapas]
categories: [Proyectos]
date: 2021-06-10T11:59:15-05:00
lastmod: 2021-06-10T11:59:15-05:00
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
projects: [Elecciones]
---

## Introducción

En México, el pasado domingo 6 de junio, se llevaron a cabo las elecciones "más grandes de la historia", con 15 gubernaturas en juego, renovación de la cámara de diputados y renovación de múltiples congresos locales. Para el caso específico de Guanajuato se eligieron presidentes municipales, diputados locales y diputados federales.

Al momento de escribir esto, los resultados oficiales aún están por salir, pero tomando la oportunidad, decidí hacer una serie de publicaciones para analizar los resultados preliminares que se tienen hasat el momento. Debido a la naturaleza de las elecciones, analizaré las 3 elecciones por separado. El análisis de las elecciones a Diputados Locales puede consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_DL) mientras que el análisis de las elecciones a Presidencias Municipales pueden consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_PM).

## Elección de Diputados Federales

Para las elecciones de Diputados Federales, el avance de las elecciones puede verse en el Programa de Resultados Electorales Preliminares 2021, en la página del [Instituto Nacional Electoral (INE)](https://prep2021.ine.mx/diputaciones/nacional/circunscripcion2/guanajuato/votos-distrito/mapa). 

Como se puede observar en dicho mapa, el PAN ganó en solitario 12 de los 15 distritos y en alianza con el PRI y el PRD (Va por México) 1 más; Morena ganó 1 distrito en solitario y ganó 1 más en alianza con el Partido Verde y con el PT (Juntos Haremos Historia). Llama mi atención que la mayoría de las candidaturas fue en solitario, excepto 2, que resultaron ganadoras: para el distrito VIII donde ganó Va por México y el XIII donde ganó Juntos Haremos Historia.

Con eso en mente, y considerando que solo hubo 2 partidos ganadores (PAN y Morena, ya sea solos o en alianza), expongo los siguientes mapas a nivel sección donde se puede observar en dónde hubo más votos para cada partido. En ambos casos agregó los resultados hipoteticos de qué hubiera ocurrido si el PAN solo se hubiera presentado con la alianza Va por México y si Morena solo se hubiera presentando bajo la alianza Juntos Haremos Historia. Lo anterior porque **si Morena se hubiera presentado en alianza para el distrito VIII, lo hubiera ganado, mientras que si el PAN se hubiera presentado en alianza para el distrito X y para el distrito XIII, también los hubiera ganado.**

### PAN

<iframe
    src='./static/dipfederales_pan.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

### Morena

<iframe
    src='./static/dipfederales_morena.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

## Balance

Ahora bien, esos mapas solo dicen donde estuvieron los votos, pero ¿dónde se decidió la elección? Para ello cree este mapa con las diferencias a favor del PAN en azul (en rojo a favor de Morena), donde se puede observar especificamente en qué zonas ganó (o en donde perdió).  

<iframe
    src='./static/dipfederales_difs.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

Destacó 2 conclusiones sencillas:
- Morena ganó principalmente en secciones rurales, aunque hay muy pocos votos en ellas. 
- Fueron más significativas las diferencias en zonas urbanas.

Si bien los resultados aquí analizados todavía son preliminares, son bastante interesantes. Corto abruptamente para continuar con el análisis de las otras elecciones. Coman frutas y verduras.
