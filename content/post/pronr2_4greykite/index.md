---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Herramientas para Pronósticos de Series de Tiempo en Python -  Parte 4: Greykite"
subtitle: "El Cometa entra al duelo de herramientas en Python."
summary: "El Cometa entra al duelo de herramientas en Python."
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
date: 2021-09-06T00:59:25-06:00
lastmod: 2021-09-06T00:59:25-06:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Foto: Iwan Shimko en [Unsplash](https://unsplash.com/photos/YgPKG3no18s)"
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

Cómo señalé en la tercera parte, una herramienta para hacer pronósticos que me mucho gusto fue [*Prophet*](https://facebook.github.io/prophet/), cuyas implementaciones pueden ver [aquí para el anterior round](https://gonzalezhomar.netlify.app/post/pronostico_3_prophet/) y [aquí para este nuevo round](https://gonzalezhomar.netlify.app/post/pronr2_3prophet/). 

Al parecer esta herramienta ha tenido un fuerte impacto en el mundo de la ciencia de datos como puede verse [aquí](https://towardsdatascience.com/time-series-analysis-with-facebook-prophet-how-it-works-and-how-to-use-it-f15ecf2c0e3a), [aquí](https://towardsdatascience.com/prophet-in-a-loop-a875516ef2f9), [aquí](https://medium.com/gousto-engineering-techbrunch/stop-using-prophet-as-a-black-box-3-ways-it-can-go-wrong-1046f6c6ec73) y [aquí](https://towardsdatascience.com/a-quick-start-of-time-series-forecasting-with-a-practical-example-using-fb-prophet-31c4447a2274) e incluso, en este último caso se convierte en la primera herramienta a utilizar.

En respuesta a esta herramienta desarrollada por Facebook, el equipo de inteligencia artificial de LinkedIn desarrollo el algoritmo *Silverkite* y un paquete de Python para implementarlo llamado [*Greykite*](https://linkedin.github.io/greykite/docs/0.1.0/html/pages/greykite/overview.html), con el cual planea competir con Prophet. Así que inspirado por [esta publicación](https://towardsdatascience.com/linkedins-response-to-prophet-silverkite-and-greykite-4fd0131f64cb) y por [esta otra](https://medium.com/geekculture/greykite-the-new-forecasting-library-from-linkedin-case-bitcoin-price-prediction-981d21e79b31), decidí incluir esta herramienta en mi duelo de pronósticos. 

## 2. *Greykite* y *Silverkite*

Al igual que *Prophet*, el algoritmo de *SilverKite* fue desarrollado para trabajar bien con series de tiempo, pues su objetivo es trabajar a escala (múltiples series), puesto que de acuerdo [al paper de *Silverkite*](https://www.arxiv-vanity.com/papers/2105.01098/), cuando este algoritmo fue desarrollado, tenía los siguientes objetivos:
- Flexibilidad: El modelo debe ser capaz de manejar series de tiempo con tendencia, estacionalidad, días feriados, quiebres, autoregresión, entre otras. Por lo tanto, se le permite al usuario seleccionar cuales de los componentes necesitan y ajustar el modelo seleccionado. No obstante, el modelo trae valores predeterminados que permiten usar *Silverkite* directamente.
- Interpretabildiad: Para *Silverkite* no solo importa el desempeño, sino que también importa su explicabilidad. Para ello, incluye gráficas y plantillas para mejorar y explicar los pronósticos con supuestos claros.
- Velocidad: *Silverkite* permite usar plantillas para obtener pronósticos de manera rápida, por lo que sus pronósticos pueden ser implementados a escala rápidamente.

A diferencia de *Prophet*, en *Silverkite* no hay una ecuación que represente el modelo predictivo. En su lugar, presentan un diagrama con los procesos que hace el algoritmo:
- En un primer paso, extrae características que puedan influir en el modelo, como días feriados, tendencia estacionalidad.
- En segundo lugar, pasa dichas características a una base apropiada (como series de Fourier que también usa *Prophet*), para un modelo aditivo.
- En tercer lugar, *Silverkite* busca quiebres en la tendencia o en la estacionalidad. 
- De las características extraídas en el segundo y tercer paso, busca un modelo de aprendizaje automático para explicar dichas variables.
- Y finalmente, de los residuales que quedan, busca un modelo de varianza condicional para capturar la volatilidad que aún persista.
- Al igual que en *Prophet*, el usuario de *Greykite*, es decir, yo, puedo incluir variables explicativas o modificar los días feriados. 

** Nota importante **
Actualmente trabajo *Python* con la distribución anaconda, puesto que desde allí me resulta muy sencillo instalar paquetes con conda, puesto que automáticamente detecta los paquetes faltantes y resuelve los conflictos. Sin embargo, al estar instalando algunos paquetes de pip, corrompí mi único ambiente (*enviroment*) y para resolverlo, la solución más fácil que encontré fue desinstalar completamente anaconda.

Dado que este paquete de *Greykite* solo se encuentra disponible en pip y no en conda, recomiendo crear un ambiente propio para su implementación. Esto evitará posibles conflictos con otros paquetes que pueden ser instalados después (como *plotly*, que funciona bastante bien con las gráficas de *Greykite*). 

```python
conda create -n myenv
conda activate myenv
pip install greykite
conda install plotly
```

La *notebook* que acompaña a esta publicación se puede encontrar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos) o la pueden ver directamente [aquí](https://nbviewer.jupyter.org/github/gonzalezhomar/articulos_pronosticos/blob/main/PronR2_4.ipynb).

## 3. Series Mensuales

De mis 2 bloques de series, ahora iniciaré con la serie mensual de IEPS a las bebidas alcohólicas. Como antes, solo dejare el análisis completo para esta serie y en el resto de las series mensuales solo dejaré los resultados.

Llama mi atención, que cada herramienta para usar *Greykite*, tiene ser especificada en la carga de paquetes:

```python
from greykite.common.data_loader import DataLoader
from greykite.framework.templates.autogen.forecast_config import ForecastConfig
from greykite.framework.templates.autogen.forecast_config import MetadataParam
from greykite.framework.templates.forecaster import Forecaster
from greykite.framework.templates.model_templates import ModelTemplateEnum
from greykite.framework.utils.result_summary import summarize_grid_search_results
from greykite.framework.input.univariate_time_series import UnivariateTimeSeries
from greykite.framework.templates.autogen.forecast_config import ModelComponentsParam
```

En general, para utilizar *Greykite* en las series mensuales, solo tengo que crear los meta parámetros que le servirán para identificar el formato de la serie: columna con la variable temporal, la variable a explicar, su frecuencia e incluso el formato de la fecha. Además modifiqué la estacionalidad para no considerar del tipo diaria y semanal, puesto que mis datos son mensuales. 

```python
metadata = MetadataParam(
    time_col="ts",
    value_col="y",
    freq="MS",
    date_format='YYYY-MM-DD'
)
custom_model_components = ModelComponentsParam(
     seasonality={
         "yearly_seasonality": "auto",
         "quarterly_seasonality": "auto",
         "monthly_seasonality": "auto",
         "weekly_seasonality": False,
         "daily_seasonality": False
     }
 )
```

Aquí destacó que los datos que necesito cargar a *Greykite* tienen una estructura similar a *Prophet*: una columna ts con el dato de fecha y una columna y con los datos de la variable a analizar. Como nota curiosa, *Prophet* realizaba el análisis de manera automática y poco me había detenido a analizar la frecuencia (M para mensual, Q de *quaterly* para trimestral); sin embargo *Greykite* es más exigente con la frecuencia, y tuve que señalar MS por *monthly start* para que fuera a inicios de mes, pues de otro modo, con la frecuencia M, el modelo no funcionaba.

### 3.1 IEPS Bebidas Alcohólicas

Con los parámetros generales para todas las series mensuales, puedo utilizar *Greykite* directamente salido de la caja con muy pocos comandos, por lo que el análisis completo para ajustar la serie de IEPS de bebidas alcohólicas se pueden hacer con los siguientes comandos:

```python
forecaster = Forecaster()
result = forecaster.run_forecast_config(
    df=iepsb,  # input data
    config=ForecastConfig(
        model_template=ModelTemplateEnum.SILVERKITE.name,
        model_components_param=custom_model_components,
        metadata_param=metadata,
        forecast_horizon=17,
        coverage=0.95
    )
)
```

    Fitting 3 folds for each of 1 candidates, totalling 3 fits
      

Con los resultados ajustados, se puede mostrar como ajusta el modelo intra muestra (backtest) con los siguientes comandos:

```python
backtest = result.backtest
fig = backtest.plot()
plotly.io.show(fig)
```
<iframe
    src='./static/gk_iepsb_back.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

Sin embargo, la parte interesante (para mí), la encuentro en los pronósticos que me arroja hacia adelante, los cuales se obtienen con el siguiente comando:

```python
forecast = result.forecast
fig = forecast.plot()
plotly.io.show(fig)
```
<iframe
    src='./static/gk_iepsb_fore.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

Y finalmente, se pueden analizar los componentes del pronóstico, con el siguiente comando:

```python
fig = forecast.plot_components()
plotly.io.show(fig)
```
<iframe
    src='./static/gk_iepsb_com.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

Si bien, no me gusto del todo los pronósticos que arroja, dejaré en la conclusión mis comentarios sobre estos resultados.

### 3.2 IEPS Cervezas

Para el caso del IEPS a las cervezas, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_iepsc.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.3 IEPS Tabacos

Para el caso del IEPS a tabacos, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_iepst.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.4 IEPS Gasolinas y Diésel

Para el caso del IEPS federal a las gasolinas y diésel, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_iepsg.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.5 IEPS Bebidas Saborizadas

Para el caso del IEPS a las bebidas saborizadas, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_iepsbs.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.6 IEPS Alimentos

Para el caso del IEPS a los alimentos de alta densidad calórica, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_iepsa.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.7 Impuesto a la Importación

Para el caso del impuesto a la importación, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_importacion.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 3.8 Ingresos Petroleros

Para el caso de los ingresos petroleros de la RFP, solo mostraré los resultados de su pronóstico:

<iframe
    src='./static/gk_petr.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

Con todos los pronósticos de las series mensuales, los extraje con el siguiente comando:

```python
petr_r=forecast.df.forecast
gk_men=pd.DataFrame({'ieps_gas': iepsg_r,
    'ieps_tabacos': iepst_r,
    'ieps_bebidas': iepsb_r,
    'ieps_cervezas': iepsc_r,
    'ieps_bebidassab': iepsbs_r,
    'ieps_alimentos': iepsa_r,
    'importacion': importacion_r,
    'rfp_petroleros': petr_r
})
gk_men.to_csv('greykite_mensuales')
```

## 4. Series Trimestrales

En general, para utilizar *Greykite* en las series trimestrales, solo tengo que volver a crear otros meta parámetros que le servirán a *Greykite* para identificar el formato de la serie: columna con la variable temporal, la variable a explicar, su frecuencia (*QS*) e incluso el formato de la fecha. Además, ahora deseo incluir 2 variables explícativas para el ISR y el IVA, que como señale en [la primera parte de esta serie](https://gonzalezhomar.netlify.app/post/pronr2_1sarimax/) son el PIB (ambas) y unas variables dummy para identificar quiebres de las series (la reforma del ISR y el incremento en la tasa del IVA, respectivamente). Esto lo hice con los siguientes comandos: 

```python
metadata = MetadataParam(
    time_col='ts',
    value_col='y',
    freq='QS',
    date_format='YYYY-MM-DD'
)
custom_model_components = ModelComponentsParam(
    seasonality={
        "yearly_seasonality": "auto",
        "quarterly_seasonality": "auto",
        "monthly_seasonality": "auto",
        "weekly_seasonality": False,
        "daily_seasonality": False
    },
    regressors=dict(
        regressor_cols=["var1", "var2"]
    )
 )
```

### 4.1 Impuesto Sobre la Renta, ISR

Con ello, y al igual que en las series mensuales, la carga para que *Greykite* haga el ajuste trimestral de la serie del ISR resulta bastante directa, solo tuve que agregar las variables explicativas:

```python
df=trim[['fecha','isr_real','pib_reale4','reformaisr']]
df.columns=['ts','y','var1','var2']
forecaster = Forecaster()
result = forecaster.run_forecast_config(
    df=df,  # input data
    config=ForecastConfig(
        model_template=ModelTemplateEnum.SILVERKITE.name,
        model_components_param=custom_model_components,
        metadata_param=metadata,
        forecast_horizon=6,
        coverage=0.95
    )
)
```

    Fitting 3 folds for each of 1 candidates, totalling 3 fits
   
El ajuste del pronóstico que me da esta herramienta me parece mejor que en las series mensuales:
   
```python
forecast = result.forecast
fig = forecast.plot()
plotly.io.show(fig)
```

<iframe
    src='./static/gk_isr.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

### 4.2 Impuesto al Valor Agregado, IVA

En cuanto a la serie trimestral del IVA, el análisis es muy similar, con los siguientes resultados:

<iframe
    src='./static/gk_iva.html'
    width='150%'
    height='600px'
    style='border:none;'>
</iframe>

Y la extracción de los resultados trimestrales es la siguiente:

```python
isr_r=forecast.df.forecast
iva_r=forecast.df.forecast
gk_trim=pd.DataFrame({'isr':isr_r,'iva': iva_r})
gk_trim.to_csv('greykite_trimestrales')
```

## 5. Conclusión

Si bien *Greykite* tiene el objetivo de competir con *Prophet*, sus pronósticos, al menos en el caso de las series mensuales, no me gustaron del todo. Pensé que tenía algo que ver con las fechas, pero luego de leer otras fuentes, veo que los pronósticos de *Greykite* son [poco vólatiles](https://www.kaggle.com/kaustubh93/time-series-forecasting-of-dogecoin-using-greykite). 

Creo que aún podría introducir ajustes a *Greykite* para que los pronósticos tengan un mejor comportamiento, pero de momento, y directamente salidos de la caja, estos fueron los resultados que arrojó. Que fue la misma situación para *Prophet*, con pronósticos directamente salidos de la caja. 

De hecho, en las series trimestrales, me gustaron los resultados de *Greykite*, lo cual creo que se debe a que introduje variables explicativas. Por tanto, quedo atento a sugerencias o recomendaciones sobre que ajustes puedo hacer.

Al final de este breve análisis, me gustó que pude implementar otra herramienta. De manera similar a *Prophet*, *Greykite* resulta en una caja negra donde se introducen datos y arroja pronósticos. En conclusión, me gustó.

Sin embargo, y como señalé en las entregas anteriores, quiero evaluar estos pronósticos en términos de qué tan cercanos resultan a la siguiente observación. En esta cuarta parte, los pronósticos para el tercer trimestre de 2021 resultaron los siguientes:

| Variable                  | Tercer Trimestre 2021   |
|---------------------------|---------------|
| ISR                       | 349,287.4 |
| IVA                       | 287,634.6 |
| IEPS Gasolinas            | 59,268.8 |
| IEPS Bebidas Alcohólicas  | 12,208.6 |
| IEPS Cervezas             | 4,101.4 |
| IEPS Tabacos              | 9,896.3 |
| IEPS Bebidas Saborizadas  | 7,642.2 |
| IEPS Alimentos            | 5,894.6 |
| Impuesto a la importación | 15,353.1 |
| Ingresos Petroleros       | 87,746.2 |
| RFP       | 839,033.1 |

Aprovechando, que el 8 de septiembre, el Gobierno Federal presentó su Iniciativa de Ley de Ingresos de la Federación para 2022, me parece oportuno extraer y comparar el pronóstico que me da *Greykite* de la RFP para 2022 (en la última parte, juntaré todos los pronósticos):

| Variable                 |Greykite |ILIF 2022 |
|---------------------------|---------------|---------------|
| ISR                       | 1,649,276.8 |1,687,013.2 |
| IVA                       | 1,126,938.8 |1,213,777.9 
| IEPS Gasolinas            | 264,023.0 |288,602.5 |
| IEPS Bebidas Alcohólicas  | 49,659.2 |46,103.1 |
| IEPS Cervezas             | 17,550.1 |20,169.2 |
| IEPS Tabacos              | 40,554.6 |42,651.0 |
| IEPS Bebidas Saborizadas  | 30,695.3 |32,950.6 |
| IEPS Alimentos            | 24,439.6 |26,962.3 |
| Impuesto a la importación | 55,796.6 |72,939.5 |
| Ingresos Petroleros       | 396,734.8 |297,818.2 |
| RFP       | 3,655,668.7 |3,728,987.5 |


Para ver la versión completa de este análisis, lo pueden consultar en mi repositorio de [Github](https://github.com/gonzalezhomar/articulos_pronosticos) o la pueden ver directamente [aquí](https://nbviewer.jupyter.org/github/gonzalezhomar/articulos_pronosticos/blob/main/PronR2_4.ipynb). Sin más por el momento, eso es to, eso es to, eso es todo amigos.