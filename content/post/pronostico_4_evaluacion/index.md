---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Pronósticos de Series de Tiempo - Parte 4: Evaluación"
subtitle: "Evaluando los 3 pronósticos de series de tiempo"
summary: "Evaluando los 3 pronósticos de series de tiempo"
authors: 
- admin
tags: 
- Series de Tiempo
- Economía
- Econometría
- Python
- Jupyter
categories: 
- Proyectos
date: 2021-08-04T12:26:50-05:00
lastmod: 2021-08-04T12:26:50-05:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Cars. Pixar, no me demandes."
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [pronosticos]
---

## 1. Introducción

Después de 3 meses en el tintero, llega la hora de evaluar como le fue a los pronósticos elaborados con diferentes metodologías para los principales impuestos de México:
* En la [parte 1](https://gonzalezhomar.netlify.app/post/pronostico_1_manual/) presente el problema, abordando el tema desde una metodología "a la vieja escuela". 
* En la [parte 2](https://gonzalezhomar.netlify.app/post/pronostico_2_autoarima/) abordé el mismo problema a través de una *notebook* de manera automatizada, con lo que llamé "la nueva escuela". 
* Y en la [parte 3](https://gonzalezhomar.netlify.app/post/pronostico_3_prophet/) presenté el mismo ejercicio, utilizando la herramienta [Prophet](https://facebook.github.io/prophet/) desarrollada por Facebook.

Las bases de datos, la sesión de Gretl y las *notebooks* con el código completo de esta serie de publicaciones se pueden encontrar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos).

## 2. Resultados

Una vez que la trílogía estuvo completa, tuve las 3 cabezas del dragón blanco de ojos azules, las 3 cajas madre, la trifuerza... en fin... arrancó la carrera. Tres meses han pasado, y la recaudación observada al primer trimestre de 2021, se compara con los pronósticos como sigue:
  
| Variable             | 1 Vieja Escuela| 2 Auto ARIMA   | 3 Prophet      |  Observado   |
|--------------------- |---------------:|---------------:|---------------:|-------------:|
| ISR                  | 484,002.95     | 403,011.84     | 493,018.41     |   441,494.98 |
| IVA                  | 234,892.56     | 256,953.12     | 223,331.36     |   272,215.81 |
| IEPS Gasolinas       | 68,678.40      | 93,464.39      | 62,136.99      |    60,824.53 |
| IEPS Tabacos         | 3,889.50       | 11,055.46      | 7,769.49       |     3,580.11 |
| IEPS Bebidas         | 4,973.40       | 5,337.24       | 5,298.17       |     4,853.84 |
| IEPS Cervezas        | 7,954.10       | 10,590.54      | 9,834.98       |     8,213.76 |
| Ingresos Petroleros  | 39,429.80      | 85,570.68      | 45,549.01      |    55,005.40 |

Y bueno... ¿cómo se lee eso? Para medir los resultados, utilizaré el error cuadrático medio, para medir la distancia entre el resultado y lo observado, quedando dicho error como sigue:

| Variable             | 1 Vieja Escuela  | 2 Auto ARIMA     | 3 Prophet        |
|--------------------- |-----------------:|-----------------:|-----------------:|
| ISR                  |  1,806,927,755.82| 1,480,951,844.91 |  2,654,664,132.65|
| IVA                  |  1,393,025,122.31|  232,949,759.91  |  2,389,689,624.36|
| IEPS Gasolinas       |  61,683,206.03   |  1,065,360,178.42|  1,722,539.90    |
| IEPS Tabacos         |  95,723.25       |  55,880,883.79   |  17,550,919.45   |
| IEPS Bebidas         |  14,293.97       |  233,673.03      |  197,426.82      |
| IEPS Cervezas        |   67,424.41      |  5,649,073.1     |  2,628,347.45    |
| Ingresos Petroleros  |  242,599,197.01  |  934,236,573.73  |  89,423,239.98   |
|--------------------- |-----------------:|-----------------:|-----------------:|
| Total                | 3,504,412,722.80 |  3,775,261,986.92|  5,155,876,230.60|

### 2.1 **ISR e IVA.** 

En el caso de las series del ISR y del IVA, el mejor modelo resultó ser el Auto ARIMA al subestimar el ISR y sobreestimar el IVA, coincidiendo con lo observado. De momento no encuentro motivo para este comportamiento, pero sospecho que con más información, los pronósticos que pueda obtener con Prophet pueden mejorar.

### 2.2 **IEPS Tabacos, Bebidas y Cervezas.** 

En este grupo de pronósticos, resultó mejor modelo la vieja escuela al obtener resultados muy cercanos a lo que realmente se registró. Consideró que esto sucedió así porque en el modelo a la vieja escuela no deje fuera las últimas observaciones, cosa que sí hice en el Auto ARIMA y el Prophet realiza de manera automática. Al considerar los últimos resultados el modelo de la vieja escuela mantiene el último comportamiento observado que es similar al comportamiento durante el trimestre que se evalúa.

### 2.3 **IEPS Gasolinas e ingresos petroleros.**

En estos pronósticos, que destacan por ser más volatiles que el resto, el mejor modelo resultó ser Prophet. Creo que esto se debe a que este modelo está diseñado para series diarias que precisamente suelen ser vólatiles. 

## 3 ¿Quién ganó?

Si bien, al sumar esos errores cuadráticos medios, el mejor modelo parece ser la vieja escuela, hay que hacer esta medición relativa a cada serie... donde al hacer la medición relativa al valor cuadrático real, también resulta mejor el modelo de la vieja escuela. Aunque si convenientemente dejó fuera la observación de Tabacos (para los 3 modelos), el mejor modelo resulta ser el Prophet. 

| Variable             | 1 Vieja Escuela  | 2 Auto ARIMA     | 3 Prophet        |
|--------------------- |-----------------:|-----------------:|-----------------:|
| ISR                  |  0.009|0.008|0.014 |
| IVA                  |  0.019|0.003|0.032|
| IEPS Gasolinas       |  0.017|0.288|0.000|
| IEPS Tabacos         |  0.007|4.360|1.369|
| IEPS Bebidas         |  0.001|0.010|0.008|
| IEPS Cervezas        |  0.001|0.084|0.039|
| Ingresos Petroleros  |  0.080|0.309|0.030|
|--------------------- |-----------------:|-----------------:|-----------------:|
| Total sin IEPS Tabacos | 0.127|0.701|0.123|

Convenientemente, porque me gusta Prophet por su simplicidad y facilidad de implementación.

## 4 ¿Conclusión?

Considerando que fácilmente puedo corregir las decisiones hechas en el Auto ARIMA que creo que afectaron el resultado, he decidido repetir este ejercicio para el segundo trimestre de 2021. Aprovecharé lo anterior para sumar más competidores a la carrera. De momento espero incluir los siguientes:
* Neural Prophet
* Greykite
* Pytorch-forecasting

Veremos si me da tiempo de seguir incluyendo más competidores. Con esto concluyo esta serie de 4 artículos sobre pronósticos y arrancaré una nueva proximamente.