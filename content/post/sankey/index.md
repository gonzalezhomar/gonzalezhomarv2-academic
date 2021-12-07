---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Diagrama de Sankey"
subtitle: "¿Cómo fluye el dinero?"
summary: "¿Cómo fluye el dinero?"
authors: 
- admin
tags: 
- Python
- Dataviz
- Blog
categories: [DataViz]
date: 2021-04-27T15:54:24-05:00
lastmod: 2021-04-27T15:54:24-05:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Gota de agua en [Unsplash](https://unsplash.com/photos/SFEvfN01-ao)"
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [Dataviz]
---

## ¿Qué es un diagrama de Sankey

Un diagrama de Sankey es un tipo específico de diagrama de flujo, en el que se puede analizar el origen de un flujo, hacia donde va, y donde la anchura de las flechas se muestra proporcional a la cantidad de flujo. Originalmente fue diseñado para medir la eficiencia en una máquina de vapor, por el irlandés Matthew Henry Phineas Riall Sanke en 1898.

Estos diagramas parecen viejos, pero son poco frecuentes... al menos en mi experiencia. Sin embargo, pueden utilizarse para analizar los flujos en diversas situaciones. Entre ellas, me interesa el flujo del dinero, de donde viene y a donde va, por lo que a continuación, presentó una implementación.

## PEF 2021

El Paquete Económico de la Federación (PEF), consiste, entre otros documentos, de una Ley de Ingresos de la Federación y un Presupuesto de Egresos de la Federación, donde se establece el origen (en la Ley de Ingresos) y el destino (Presupuesto de Egresos) de los recursos que componen las finanzas públicas del Gobierno Federal de México.

Tomando los totales de la Ley de Ingresos, y la base de datos abiertos del presupuesto de egresos disponible [la página de transparencia presupuestaria](https://www.transparenciapresupuestaria.gob.mx/en/PTP/Datos_Abiertos), pude elaborar esta gráfica con el flujo estimado de las finanzas públicas a nivel nacional de México:

<iframe
    src='./static/PEF2021_Sankey.html'
    width='100%'
    height='1000px'
    style='border:none;'>
</iframe>

Y ya... eso es todo por ahora. Por el momento, ¡que las fuerzas los acompañe!