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

Este proyecto tiene distintas fuentes. En mis clases de econometría me enseñaron diversas herramientas para hacer pronósticos, siendo la más importantes el clásico modelo ARIMA. Para correrlo, aprendí diferentes herramientas: EViews, Gretl, STATA e incluso Matlab. Sin embargo, nunca ví que se detuvieran analizar si estas herramentas podrían generar diferencias. Si corro el mismo modelo ¿generará diferencias entre herramientas?

Por otro lado, para evaluar los pronósticos, siempre me enseñaron medidas estadísticas intra muestra: suma cuadrada de los errores, raíz de la suma cuadrada de los errores, y la desviación cuadrada de los errores respecto del error medio cuadrado (la famosa $R^2$). O a veces evaluaban el modelo quitando la última observación, actualizando los resultados del modelo y viendo el comportamiento intra muestra. Ninguna de las 2 anteriores medidas me gusta porque creo que ese no es el objetivo de hacer un pronóstico: tener una estimación lo que va a pasar. Es decir, ¿por qué revisar el pasado si lo que me interesaba era el futuro? 

Planteado de otra forma, el objetivo del análisis de series de tiempo es obtener una estimación de lo que va a pasar. Entonces, me parece que hay un problema de fondo al evaluar los modelos con las observaciones previas, cuando lo que quiero es evaluar los modelos en función de los pronósticos que generan. Por ello, decidí evaluar cómo le fue a cada pronóstico con las observaciones futuras. 

En un primer ejercicio, utilicé 3 herramientas:
- En la [parte 1](https://gonzalezhomar.netlify.app/post/pronostico_1_manual/) abordé el tema "a la vieja escuela" usando Gretl. 
- En la [parte 2](https://gonzalezhomar.netlify.app/post/pronostico_2_autoarima/) automaticé todo con una *notebook*  en Python a "la nueva escuela". 
- En la [parte 3](https://gonzalezhomar.netlify.app/post/pronostico_3_prophet/) utilicé una nueva herramienta que encontré llamada [Prophet](https://facebook.github.io/prophet/) desarrollada por Facebook.

Sin embargo, en este primer ejercicio, no quedé conforme con los [resultados](https://gonzalezhomar.netlify.app/post/pronostico_4_evaluacion/), por lo que hice un segundo round con nuevos competidores:
- En la [parte 1](https://gonzalezhomar.netlify.app/post/pronr2_1sarimax/) abordé el tema con el modelo SARIMAX automatizando todo con una *notebook*  en Python. 
- En la [parte 2](https://gonzalezhomar.netlify.app/post/pronr2_2holtwinters/) utilicé otro método estadístico para hacer predicciones, que consiste en descomponer la serie: el método Holt-Winters.
- En la [parte 3](https://gonzalezhomar.netlify.app/post/pronr2_3prophet/) repetí el análisis con [Prophet](https://facebook.github.io/prophet/) que usa herramientas estadísticas.
- En la [parte 4](https://gonzalezhomar.netlify.app/post/pronr2_4greykite/) incluí una herramienta desarrollada por LinkedIn, llamada [Greykite](https://linkedin.github.io/greykite/docs/0.1.0/html/pages/greykite/overview.html).
- En la [parte 5](https://gonzalezhomar.netlify.app/post/pronr2_5neuralprophet/) incluí un hermano de Prophet llamado [NeuralProphet](https://github.com/ourownstory/neural_prophet) similar a Prophet, pero que utiliza redes neuronales.

La primer evaluación de este segundo round, la pueden consultar aquí:
![Evaluación](https://gonzalezhomar.netlify.app/post/pronr2_6eval1/)

El contenido de este proyecto se puede encontrar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos).
