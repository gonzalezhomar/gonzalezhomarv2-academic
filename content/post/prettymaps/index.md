---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Probando Prettymaps"
subtitle: "Jugando con el proyecto *Prettymaps*"
summary: "Jugando con el proyecto *Prettymaps*"
authors: 
- admin
tags: 
- Series de Tiempo
- Economía
- Econometría
- Python
- Jupyter
categories: 
date: 2021-09-23T17:45:39-05:00
lastmod: 2021-09-23T17:45:39-05:00
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
projects: []
---

## 1. Introducción

¿Alguna vez han visto algo y han dicho "¡quiero hacerlo!"? Pues me tope con este tweet y me sucedió exactamente eso:

{{< tweet 1430555174230233088 >}}

{{< tweet 1431287672488677377 >}}

Sin embargo, ¡ah, la instalación! Eso fue lo complicado.

## 2. Instalación

El detalle es que prettymaps no es una librería de Python, es un proyecto que se encuentra en Github [aquí](https://github.com/marceloprates/prettymaps). Siguiendo su instalación, debería de ser muy fácil corriendo la siguiente celda:

```python
! pip install git+https://github.com/abey79/vsketch#egg=vsketch
! pip install git+https://github.com/marceloprates/prettymaps.git
```

Desde que vi que el comando para instalar es con **pip** y no en **conda**, cree un ambiente para poder probarlo sin arruinar el resto de los programas que uso.

```python
conda create -n pmaps
conda activate pmaps
conda install jupyterlab
jupyter lab
```

En la ventana de **jupyter** corrí la celda de instalación, pero aún así no funcionó:

```python
! pip install git+https://github.com/abey79/vsketch#egg=vsketch
! pip install git+https://github.com/marceloprates/prettymaps.git
```

Tuve que instalar Fiona y GDAL, descargando sus correspondientes versiones de [aquí](https://www.lfd.uci.edu/~gohlke/pythonlibs/). Los depósite en mis documentos y en la terminal de python corrí:

```python
pip -m install 'GDAL‑3.3.2‑cp38‑cp38‑win_amd64.whl'
pip -m install 'Fiona‑1.8.20‑cp38‑cp38‑win_amd64.whl'
```

Luego corrí la celda de instalación y parecía funcionar porque ya no me generó error, pero la celda de importación no funcionó: 

```python
import sys; sys.path.append('../')
import warnings
warnings.filterwarnings('ignore')
# Prettymaps
from prettymaps import *
# Vsketch
import vsketch
# OSMNX
import osmnx as ox
# Matplotlib-related
import matplotlib.font_manager as fm
from matplotlib import pyplot as plt
from descartes import PolygonPatch
# Shapely
from shapely.geometry import *
from shapely.affinity import *
from shapely.ops import unary_union
```

Me marcaba que no estaba instalado shapely, así que tuve que desinstalar *shapely* y volverlo a instalar:

```python
pip uninstall shapely
conda install shapely
```

Y finalmente, voila, ¡importación correcta!


## 3. Galería

Disculpe usted, mi sesgo guanajuatense.

### Ciudad de México

![imagen](./maps/cdmx_1.png)
![imagen](./maps/cdmx_2.png)

### Tijuana
![imagen](./maps/tijuana_3.png)
![imagen](./maps/tijuana_4.png)

### Ciudad Juárez
![imagen](./maps/cdjuarez_1.png)
![imagen](./maps/cdjuarez_2.png)

### Monterrey
![imagen](./maps/monterrey_2.png)
![imagen](./maps//monterrey_3.png)

### Guadalajara
![imagen](./maps/guadalajara_3.png)
![imagen](./maps/guadalajara_4.png)

### León
![imagen](./maps/leon_1.png)
![imagen](./maps/leon_2.png)

### Puebla
![imagen](./maps/puebla_2.png)
![imagen](./maps/puebla_3.png)

### Querétaro
![imagen](./maps/qro_1.png)
![imagen](./maps/qro_2.png)

### San Luis Potosí
![imagen](./maps/slp_2.png)
![imagen](./maps/slp_4.png)

### Guanajuato
![imagen](./maps/guanajuato_3.png)
![imagen](./maps/guanajuato_4.png)

### San Miguel de Allende
![imagen](./maps/allende_2.png)
![imagen](./maps/allende_4.png)

### Irapuato
![imagen](./maps/irapuato_2.png)
![imagen](./maps/irapuato_4.png)

### Abasolo
![imagen](./maps/abasolo_3.png)
![imagen](./maps/abasolo_4.png)
