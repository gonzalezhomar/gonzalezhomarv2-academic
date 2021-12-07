---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Pronosticos"
subtitle: "Estimando proyecciones de series de tiempo"
summary: "Estimando proyecciones de series de tiempo"
authors: 
- admin
tags: 
- Series de Tiempo
- Economía
- Econometría
- Python
- Jupyter
categories: 
- Econometría
date: 2021-04-06T16:59:03-06:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "[Unsplash](https://unsplash.com/photos/9HI8UJMSdZA)"
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

## Proyecto

Esta es un idea que vino a mi, gracias a diferentes fuentes. En mis clases de econometría me enseñaron diversas herramientas para hacer pronósticos, siendo la más importantes el clásico modelo ARIMA. Para correrlo, aprendí diferentes herramientas (nunca lo hice manualmente): EViews, Gretl, STATA e incluso Matlab. Sin embargo, nunca ví que se detuvieran analizar si estas herramentas podrían generar diferencias. Si corro el mismo modelo ¿generará diferencias entre herramientas?

Por otro lado, para evaluar los pronósticos, siempre me enseñaron medidas estadísticas intra muestra: suma cuadrada de los errores, raíz de la suma cuadrada de los errores, y la desviación cuadrada de los errores respecto del error medio cuadrado (la famosa $R^2$). O a veces evaluaban el modelo quitando la última observación, actualizando los resultados y viendo el comportamiento intra muestra. Ninguna de las 2 anteriores medidas me gusta porque creo que ese no es el objetivo de hacer un pronóstico: tener una estimación lo que va a pasar. Es decir, ¿por qué revisar el pasado si lo que me interesaba era el futuro? 

A raíz de las 2 preguntas anteriores, decidí estimar algunas series y en tres meses que tenga una nueva observación, evaluaré cómo le fue a cada pronóstico. Para ello, me concentraré en 3 herramientas:
- En la [parte 1](https://gonzalezhomar.netlify.app/post/pronostico_1_manual/) abordaré el tema "a la vieja escuela" usando Gretl. 
- En la [parte 2](https://gonzalezhomar.netlify.app/post/pronostico_2_autoarima/) automatizaré todo con una *notebook*  en Python a "la nueva escuela". 
- En la [parte 3](https://gonzalezhomar.netlify.app/post/pronostico_3_prophet/) utilizaré una nueva herramienta que encontré llamada [Prophet](https://facebook.github.io/prophet/) desarrollada por Facebook.

El contenido de este proyecto se puede encontrar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos).

Los resultados los publicaré en 3 meses aquí mismo. Si de aquí a 3 meses, decido incluir otra estimación la agregaré a la baraja.