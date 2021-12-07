---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Elecciones 2021 en Guanajuato, Parte 2: Diputados Locales"
subtitle: "Un pequeño análisis geográfico de las elecciones a Diputados Locales en Guanajuato"
summary: "Un pequeño análisis geográfico de las elecciones a Diputados Locales en Guanajuato"
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

Al momento de escribir esto, los resultados oficiales aún están por salir, pero tomando la oportunidad, decidí hacer una serie de publicaciones para analizar los resultados preliminares que se tienen hasat el momento. Debido a la naturaleza de las elecciones, analizaré las 3 elecciones por separado. El análisis de las elecciones a Diputados Federales puede consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_DF) mientras que el análisis de las elecciones a Presidencias Municipales pueden consultarse [aquí](https://gonzalezhomar.netlify.app/post/prep2021_PM).

## Elección de Diputados Locales

Para las elecciones de Diputados Locales, el avance de las elecciones puede verse en el Programa de Resultados Electorales Preliminares 2021, en la página del [Instituto Electoral del Estado de Guanajuato (IEEG)](https://prepgto2021.ieeg.mx/#/diputaciones/entidad/votos-entidad/mapa).

Como se puede observar en dicho mapa, el PAN ganó en solitario 21 de los 22 distritos mientras que Morena ganó 1 distrito. A diferencia de las elecciones a Diputados Federales, en lo local la única alianza que se presentó, para todos los distritos en juego, fue entre el PRI y el PRD. 

De origen tengo 2 conclusiones similares al análisis hecho para Diputados Federales: 
- Si el PAN se hubiera presentado en alianza con el PRI y el PRD para el distrito XIV, y Morena no hubiera hecho alianza, lo hubiera ganado.
- De maner similar si Morena hubiera ido en alianza con el Partido Verde y el PT para los distritos XIII, XIX, XVII, XX y XXII, dicha alianza hubiera podido ganar al PAN esos distritos.

También llama mi atención como se compara con el mapa de los [distritos federales](https://prep2021.ine.mx/diputaciones/nacional/circunscripcion2/guanajuato/votos-distrito/mapa) con el mapa de los [distritos locales](https://prepgto2021.ieeg.mx/#/diputaciones/entidad/votos-entidad/mapa). Principalmente en el centro sur del Estado, los distritos resultaron inversos: 
- A nivel federal el PAN perdió los distritos X y XIII donde ganó Morena, pero a nivel de Diputación Local ganó las mismas zonas geográficas.
- Mientras que en el distrito federal VIII donde sí ganó el PAN, se perdió el distrito local XIV que coincide geográficamente con Salamanca.

Considerando que solo hubo 2 partidos ganadores (PAN y Morena), repito los mapas a nivel sección donde se puede observar en dónde hubo más votos para cada partido por separado:

### PAN

<iframe
    src='./static/diplocales_pan.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

### Morena

<iframe
    src='./static/diplocales_morena.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

## Balance

Ahora bien, esos mapas solo dicen donde estuvieron los votos, pero ¿dónde se decidió la elección? Para ello cree este mapa con las diferencias a favor del PAN en azul (en rojo a favor de Morena), donde se puede observar especificamente en qué zonas ganó (o en donde perdió).  

<iframe
    src='./static/diplocales_difs.html'
    width='100%'
    height='600px'
    style='border:none;'>
</iframe>

Se repiten las conclusiones federales:
- Morena ganó principalmente en secciones rurales, aunque hay muy pocos votos en ellas. 
- Fueron más significativas las diferencias en zonas urbanas.

Al comparar los resultados en los 2 niveles, se observa que los votos fueron más o menos consistentes, pero la diferencia que genera sumar diferentes zonas a diferentes distritos, fue la diferencia en los resultados. Sobre más de este tema sugiero leer el tema ["Gerrymandering"](https://es.wikipedia.org/wiki/Gerrymandering).

Si bien los resultados aquí analizados todavía son preliminares, son bastante interesantes. Corto abruptamente para continuar con el análisis de la última elección que se llevo a cabo en Guanajuato. Hagan ejercicio.