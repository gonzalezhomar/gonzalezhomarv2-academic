---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Elecciones 2021 en Guanajuato, Parte 3: Presidentes Municipales"
subtitle: "Un pequeño análisis geográfico de las elecciones a Presidentes Municipales en Guanajuato"
summary: "Un pequeño análisis geográfico de las elecciones a Presidentes Municipales en Guanajuato"
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

Al momento de escribir esto, los resultados oficiales aún están por salir, pero tomando la oportunidad, decidí hacer una serie de publicaciones para analizar los resultados preliminares que se tienen hasat el momento. Debido a la naturaleza de las elecciones, analizaré las 3 elecciones por separado. El análisis de las elecciones a Diputados Federales puede consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_DF) mientras que el análisis de las elecciones a Diputados Locales pueden consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_DL).

## Elección de Presidentes Municipales

Para las elecciones de Presidentes Municipales, el avance de las elecciones puede verse en el Programa de Resultados Electorales Preliminares 2021, en la página del [Instituto Electoral del Estado de Guanajuato (IEEG)](https://prepgto2021.ieeg.mx/#/ayuntamientos/entidad/votos-entidad/mapa). 

Como se puede observar en dicho mapa, el PAN ganó 22 Presidencias Municipales, el PRI 3, el PRD 2, el Partido Verde 3, Movimiento Ciudadano 2, Morena 3, Nueva Alianza 1, Redes Sociales Progresistas 2, la alianza PRI PRD ganó 7 y el último Municipio fue ganado por un candidato independiente. Claramente, estos resultados son mucho más diversos que para los Diputados Federales o Locales.

Por lo anterior, tengo que analizar los votos por separado. Dejo los siguientes mapas: PAN, Morena, a la alianza PRI-PRD (sin distinguir si ganaron por separado o en alianza) y en un mapa los otros partidos. En cuanto a este último mapa, no separó los partidos para ser más conciso en la información, pero no quiero demeritar las victorias de cada partido en lo local.

### PAN

<iframe
    src='./static/ayuntamientos_pan.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

### Morena

<iframe
    src='./static/ayuntamientos_morena.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

### PRI-PRD

<iframe
    src='./static/ayuntamientos_priprd.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

### Resto de los Partidos

<iframe
    src='./static/ayuntamientos_otros.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

## Balance

Con una diversidad de resultados tan amplia resulta complicado llegar a conclusiones sobre estos resultados. Por lo anterior, y derivado de que en las Diputaciones Locales Morena tuvo un crecimiento fuerte en el centro sur del estado, me preguntó ¿qué hubiera pasado si hubieran competido las alianzas? 

- Si hubieran competido las alianzas, la alianza Va x México sí le hubiera podido ganar a Juntos Haremos Historia en Silao y en Yuriria; además de que también le hubiera ganado a Santiago Maravatío al candidato independiente que resultó ganador.
- Curiosamente, la alianza Juntos Haremos Historia no alcanza a revertir ninguno de los Municipios donde ganó el PAN.

<iframe
    src='./static/ayuntamientos_jhh.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

Si bien los resultados aquí analizados todavía son preliminares, son bastante interesantes. Corto abruptamente para publicar esta serie de publicaciones. Es cuanto, jeje.