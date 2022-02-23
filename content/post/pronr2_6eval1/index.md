---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Herramientas para Pronósticos de Series de Tiempo en Python -  Parte 6: Evaluación"
subtitle: "Primera Evaluación de los Competidores"
summary: "Primera Evaluación de los Competidores"
authors: 
- admin
tags: 
- Series de Tiempo
- Economía
- Econometría
- Python
- Jupyter
categories: 
- Pronósticos
date: 2022-02-21T12:33:32-06:00
lastmod: 2022-02-21T12:33:32-06:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Cars. Pixar, no me demandes... otra vez."
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

Hace mucho tiempo, en una galaxia muy lejana, comencé este proyecto para hacer pronósticos de series de tiempo, para evaluar los resultados de diferentes modelos y metodologías, desde una óptica *ex-post*. Es decir, quiero evaluar los modelos de series de tiempo, en función de los pronósticos que generan y no en función del ajuste histórico.

Resumiendo el proyecto, utilicé difentes herramientas para hacer pronósticos de los principales impuestos que componen una bolsa llamada Recaudación Federal Participable (RFP). Dicha bolsa es importante para las Entidades Federativas, puesto que a partir de la RFP se determinan los ingresos por participaciones que reciben las Entidades Federativas y los Municipios.

Han pasado algunos meses, pero apenas tengo una nueva observación, por lo que veamos como le fue a los competidores:
- [SARIMAX](https://gonzalezhomar.netlify.app/post/pronr2_1sarimax/)
- [Holt-Winters](https://gonzalezhomar.netlify.app/post/pronr2_2holtwinters/)
- [Prophet](https://gonzalezhomar.netlify.app/post/pronr2_3prophet/)
- [Greykite](https://gonzalezhomar.netlify.app/post/pronr2_4greykite/)
- [Neural Prophet](https://gonzalezhomar.netlify.app/post/pronr2_5neuralprophet/)

Las bases de datos y las notebooks con el código completo de esta serie de publicaciones se pueden encontrar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos).

## 2. Resultados

Luego de tener estos modelos guardados en el cajón, para el tercer trimestre de 2021 tenía los siguientes pronósticos:

| Modelo                  |SARIMAX    |Holt Winters |Prophet    |Greykite  |Neural Prophet|
|---------------------------|-----------|-------------|-----------|----------|--------------|
| Impuesto Sobre la Renta   | 330,019.5 |345,776.8    |335,920.2  |349,287.4 |317,209.1     |
| Impuesto al Valor Agregado| 293,288.9 |298,731.4    |290,548.8  |287,634.6 |289,094.0     |
| IEPS Gasolinas            | 55,057.4  |66,563.0     |59,340.4   |59,268.8  |58,249.0      |
| IEPS Bebidas Alcohólicas  | 18,463.4  |8,606.5      |17,439.8   |12,208.6  |13,144.5      |
| IEPS Cervezas             | 3,424.7   |3,848.7      |3,497.6    |4,101.4   |3,868.4       |
| IEPS Tabacos              | 10,966.3  |12,231.3     |10,651.0   |9,896.3   |10,741.1      |
| IEPS Bebidas Saborizadas  | 8,211.8   |8,213.4      |8,518.7    |7,642.2   |8,419.8       |
| IEPS Alimentos            | 5,211.3   |6,194.1      |6,323.5    |5,894.6   |5,851.0       |
| Impuesto a la importación | 19,552.1  |19,784.7     |20,128.9   |15,353.1  |19,096.3      |
| Ingresos Petroleros       | 62,891.3  |97,973.4     |56,735.0   |87,746.2  |63,146.3      |
| **RFP** | 807,086.7 |867,923.4    |809,103.8  |839,033.1 |788,819.5  |

E inclusive, ya tenía los siguientes pronósticos para el cuarto trimestre de 2021:

| Modelo           |SARIMAX |Holt Winters |Prophet |Greykite |Neural Prophet |
|---------------------|---------------|---------------|---------------|---------------|---------------|
| Impuesto Sobre la Renta  | 305,368.3 |360,741.3 |294,397.1 |353,830.9 |287,311.3 |
| Impuesto al Valor Agregado | 269,391.5 |287,947.5 |267,074.9 |259,987.7 |264,339.2 |
| IEPS Gasolinas            | 58,821.2 |69,444.1 |59,938.7 |64,023.8 |61,022.1 |
| IEPS Bebidas Alcohólicas  | 9,582.1 |13,496.9 |11,372.3 |11,975.3 |10,391.8 |
| IEPS Cervezas             | 4,002.5 |4,904.6 |4,013.9 |4,132.6 |4,171.6 |
| IEPS Tabacos              | 10,323.2 |12,089.0 |11,277.6 |9,885.0 |10,470.1 |
| IEPS Bebidas Saborizadas  | 7,592.5 |7,631.0 |7,598.0 |7,472.5 |7,785.9 |
| IEPS Alimentos            | 5,221.4 |6,163.0 |5,815.3 |5,754.3 |5,654.2 |
| Impuesto a la importación | 19,024.9 |20,255.7 |19,804.0 |13,705.8 |19,169.2 |
| Ingresos Petroleros       | 60,787.7 |119,636.0 |42,998.7 |99,154.6 |48,834.8 |
| **RFP**                   | 750,115.2 |902,309.2 |724,290.5 |829,922.4 |719,150.3 |

Antes de adelantarnos y ver como le fue a la RFP, veamos cómo le fue estas proyecciones para cada uno de los impuestos, utilizando la clásica medida de la suma de los errores cuadrados.

### 2.1 Impuesto Sobre la Renta

En cuanto al Impuesto Sobre la Renta (ISR), que es el principal componente de la RFP, el pronóstico más cercano fue el que obtuve con *SARIMAX*. 

![png](1.png)
    
### 2.2 Impuesto al Valor Agregado

En cuanto al Impuesto al Valor Agregado (IVA), que es el segundo principal componente de la RFP, el pronóstico más cercano fue el que obtuve con *SARIMAX* seguido muy de cerca por *Prophet* y *Neural Prophet*. 

![png](2.png)
    
### 2.3 IEPS Gasolinas y Diésel

En cuanto al Impuesto Especial sobre Producción y Servicios (IEPS) a la venta final de gasolinas y diésel, el pronóstico más cercano fue también con *SARIMAX*... lo que no me gusta porque la proyección de este modelo es una simple constante. 

![png](3.png)
    
### 2.4 IEPS Bebidas Alcohólicas

En cuanto al IEPS a las bebidas alcohólicas, el pronóstico más cercano fue *Holt-Winters*. 

![png](4.png)
    
### 2.5 IEPS Cervezas

En cuanto al IEPS a las cervezas, el pronóstico más cercano fue *Holt-Winters*. 

![png](5.png)
    
### 2.6 IEPS Tabacos

En cuanto al IEPS a los tabacos, el pronóstico más cercano fue *Holt-Winters*. 
 
![png](6.png)
    
### 2.7 IEPS Bebidas Saborizadas

En cuanto al IEPS a las bebidas saborizadas, el pronóstico más cercano fue *Neural Prophet*. 

![png](7.png)
    
### 2.8 IEPS Alimentos

En cuanto al IEPS a los alimentos de alta densidad calórica, el pronóstico más cercano fue *Holt-Winters*. 

![png](8.png)
    
### 2.9 Impuesto a la Importación

En cuanto al impuesto a la importación, el pronóstico más cercano fue *Holt-Winters*.
    
![png](9.png)
    
### 2.10 Ingresos Petroleros

En cuanto a los ingresos petroleros que forman parte de la RFP, el pronóstico más cercano fue *SARIMAX*. 
    
![png](10.png)
    
### 3 ¿Y quién ganó?

En cuanto a la estimación del gran total de la Recaudación Federal Participable, el ganador en esta primera observación es el modelo *SARIMAX*, seguido muy de cerca por *Prophet* y *Neural Prophet*.
    
![png](11.png)

Pero ¡no tan rápido! Si bien, el modelo *SARIMAX* tuvo una mejor precisión ello es porque no incluí todas las series de la RFP en mi análisis. Si me enfocó sólo en las series que estoy pronósticando, es decir, una RFP que solo tenga estas series, *Neural Prophet* resulta más cercana:

![png](12.png)

O en cambio, puedo hacer la suma cuadrada de los errores de cada serie, para considerar el total de los errores... dónde también gana *SARIMAX*:

![png](13.png)

## 4. Continuará

Si bien, en el objetivo original de estimar la RFP ganó el módelo *SARIMAX*, en general, me parece que los modelos generaron muy buenos pronósticos de la RFP, pues se ajustaron bastante bien a lo observado realmente, por lo que no actualizaré las proyecciones, sino que continuaré evaluando estos mismos pronósticos para el siguiente trimestre. Para la siguiente observación estimó lo siguiente:

| Modelo                |SARIMAX |Holt Winters |Prophet |Greykite |Neural Prophet |
|---------------------|---------------|---------------|---------------|---------------|---------------|
| Impuesto Sobre la Renta   | 449,758.6 |537,930.0 |474,215.9 |462,189.4 |471,972.0 |
| Impuesto al Valor Agregado| 300,399.1 |325,159.3 |308,639.2 |302,894.4 |309,002.8 |
| IEPS Gasolinas            | 58,821.2 |72,066.7 |64,951.7 |64,913.4 |61,211.1 |
| IEPS Bebidas Alcohólicas  | 19,604.8 |15,141.1 |20,496.2 |12,402.3 |14,190.1 |
| IEPS Cervezas             | 5,732.4 |6,029.8 |5,736.0 |4,311.1 |4,979.9 |
| IEPS Tabacos              | 9,656.5 |12,206.5 |9,642.6 |9,987.8 |10,368.8 |
| IEPS Bebidas Saborizadas  | 7,118.7 |6,963.3 |7,235.6 |7,524.3 |7,079.9 |
| IEPS Alimentos            | 5,647.7 |7,487.2 |5,697.2 |6,003.0 |6,405.1 |
| Impuesto a la importación | 18,355.7 |18,510.7 |18,054.2 |13,799.0 |18,264.4 |
| Ingresos Petroleros       | 60,936.6 |99,150.4 |38,450.3 |99,167.3 |44,805.8 |
| **RFP**       | 936,031.3 |1,100,645.0 |953,118.9 |983,191.8 |948,280.0 |

Sin más por el momento, nos vemos en 3 meses más... o en 6. Que siga la carrera, y ¡date prisa Gokú!
