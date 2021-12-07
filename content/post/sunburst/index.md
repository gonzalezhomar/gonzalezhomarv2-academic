---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Sunburst"
subtitle: "Una mejor gráfica de pastel"
summary: "Una mejor gráfica de pastel"
authors: 
- admin
tags: 
- Python
- Dataviz
- Blog
date: 2021-04-27T17:33:42-05:00
lastmod: 2021-04-27T17:33:42-05:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Sunburst en [Unsplash](https://unsplash.com/photos/QnCpHhS-4AE)"
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [Dataviz]
---

## Sunburst o una mejor gráfica de pastel

Las gráficas de pastel son populares para mostrar partes de un todo, y son bastante populares. En mi busqueda de un *dashboard*, me tope con esta publicación de [Medium](https://towardsdatascience.com/how-i-created-a-sunburst-chart-using-javascript-to-visualize-covid-19-data-4ef27b45af8a), donde se presenta el código para hacer una gráfica sunburst o mancha solar.

Este tipo de gráfica es como un gráfico de pastel, con diferentes niveles, y muy buena interactividad, por lo que me gusto y me dispuse a hacer una implementación.

## Gasto Federalizado

Para este caso, aplique el código anterior a las Transferencias del Gobierno Federal a Entidades Federativas y Municipios disponibles en la página de estadísticas oportunas de la Secretaría de Hacienda y Crédito Público disponible [aquí](http://presto.hacienda.gob.mx/EstoporLayout/baseDatos.jsp). 

Después de filtrar los datos para 2020, eliminar lineas que se duplican, agruparlos a nivel nacional y convertirlos a formato json, el gasto federalizado se puede ver como sigue:

<iframe height="442" style="width: 100%;" scrolling="no" title="CopySunburst" src="https://codepen.io/gonzalezhomar/embed/zYKMmrR?height=442&theme-id=light&default-tab=result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/gonzalezhomar/pen/zYKMmrR'>CopySunburst</a> by OMAR HUMBERTO GONZALEZ AVILA
  (<a href='https://codepen.io/gonzalezhomar'>@gonzalezhomar</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

Y ya... eso es todo por ahora. Por el momento, ¡que las fuerzas los acompañe! Sí... copié y pegué esta línea de mi post anterior, por favor no me demanden.