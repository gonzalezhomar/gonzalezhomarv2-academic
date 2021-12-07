---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Sobre Notebooks y Ciencia de Datos"
subtitle: "Un poco de divagaciones, o por qué inicié un blog, parte 2."
summary: "Un poco de divagaciones, o por qué inicié un blog, parte 2."
authors: 
- admin
tags: 
- Jupyter
- Ciencia de Datos
- Programación
categories:
- Blog
date: 2021-04-05T09:02:41-06:00
lastmod: 2021-04-05T09:02:41-06:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Película The Matrix. Warner no me demandes."
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

Estos días tuve un poco de tiempo, así que me propusé a hacer esta publicación que tenía rato esperando. Como señale en [mi primer blog](https://gonzalezhomar.netlify.app/post/mi_blog/), me decidí a escribir para aprender a través de publicaciones donde practicó diferentes abilidades, para practicar el hábito de la escritura, y finalmente, para concluir proyectos y resultados, *get thing done*. ¿Cómo todo se conecto para resultar en este blog? Llegue a esto, a través de 2 fuentes principales:
un artículo sobre *notebooks* y Medium.

## 2. *Notebooks*

Con mi historial académico de economista y matemático, estaba familiarizado con los artículos científicos. Básicamente son piezas de investigación, que generan nuevo conocimiento, comprueban alguna teoría, estudian casos particulares o comentan sobre hallazgos previos. Los artículos se envían a revistas académicas, y en la mayoría de los casos, otros investigadores son quienes revisan que su contenido sea correcto (*peer-reviewed*), y si los resultados son buenos, la revista los publica. En teoría, eso debería pasar pero hay casos donde las [revistas publican cualquier cosa a cambio de dinero](https://www.researchgate.net/publication/343066384_Cyllage_City_COVID-19_Outbreak_Linked_to_Zubat_Consumption), o donde [existen muchos prejuicios para publicar](https://twitter.com/cesifoti/status/1364699994012459009). No confundir las anteriores revistas, con otras revistas que publican [articulos satiricos.](https://www.researchgate.net/publication/283151480_A_Phylogeny_and_Evolutionary_History_of_the_Pokemon)

Sin embargo, este artículo lo leí hace más de 2 años, y aún lo sigo revisitando porque marco un antes y un después en cómo pienso acerca de la academia: [el artículo científico es obsoleto, esto es lo que sigue](https://www.theatlantic.com/science/archive/2018/04/the-scientific-paper-is-obsolete/556676/). Resulta que este modelo de artículo científico data de los 1600s y desde entonces han sufrido pocos cambios: la cantidad de revistas científicas ha explotado, los artículos ahora se publican en línea y hoy en día casi toda la investigación en la frontera del conocimiento está al alcance de una busqueda. Lamentablemente, entre más avanza la ciencia es más díficil comunicar los resultados; e inclusive aún y cuando el análisis se hace a través de computadoras (análisis de datos, gráficas, simulaciones, etc.), las publicaciones terminan en un PDF que es una simulación de una hoja de papel.

Para llenar ese hueco, surgió un gran avance en el análisis de datos y las publicaciones científicas, las *notebooks*, de las cuales existen muchas versiones: [Mathematica y sus notebooks](https://www.wolfram.com/mathematica/?source=nav), [código vivo de Maltab](https://la.mathworks.com/help/matlab/matlab_prog/live-script-file-format.html), [RStudio y sus notebooks](https://rmarkdown.rstudio.com/lesson-10.html), [Google Colab](https://www.datahack.es/blog/big-data/google-colab-para-data-science/) y el que se ha convertido en mi favorito [Jupyter](https://jupyter.org), donde se puede programar código no sólo en Python, sino en múltiples lenguajes. Aunque Mathematica y Matlab dependen de licencias para poder usarse, Colab, Jupyter y RStudio son de uso libre, completamente gratuitos. 

En general, las *notebooks* consisten en parte de texto, con código que se ejecuta allí mismo *código vivo*, lo cual permite realizar análisis complicados, ver los resultados allí mismo y todo en una misma interfaz. Al poder consultarse en línea, el artículo concluye, y me convence que este es el futuro de los artículos científicos. Falta camino por recorrer, pero pueba de ello es que la publicación acerca del descubrimiento de ondas gravitacionales, se hizo con [Jupyter](https://hub-binder.mybinder.ovh/user/losc-tutorial-l-_event_tutorial-owh0x056/notebooks/index.ipynb).

Y no solo eso, ahora hay millones de *notebooks* disponibles en [Github](https://github.com/topics/jupyter-notebook) (número exagerado por el autor), libros completos escritos en Jupyter como este de [Manual de ciencia de datos en Python](https://github.com/jakevdp/PythonDataScienceHandbook) e incluso se pueden dictar cursos en este formato (al final del artículo de The Atlantic se menciona uno de ellos).

## 3. Medium

Hace apróximadaente 1 año, me tope con la plataforma de [*Medium*](https://medium.com/about), que es una plataforma de blogs y como soy fan de la lectura, quede enganchado con el contenido que allí aparece sobre diversos temas: escritura, programación, finanzas, crecimiento personal, experiencias, e incluso entrevistas. 

Dentro de este universo, me llamó mucho la atención la serie [*Towards Data Science*](https://towardsdatascience.com/about), que trata de artículos de ciencia de datos. Si bien no son artículos científicos, son artículos introductorios donde las personas comparten pequeños proyectos, hablan de distintas paqueterías, prueban nuevas herramientas y comparten abiertamente su conocimiento. 

Entre estos proyectos, muchos precisamente fueron escritos precisamente en *notebooks* e inclusive hay uno que trata precisamente de cómo instalar [Anaconda](https://medium.com/@GalarnykMichael/install-python-anaconda-on-windows-2020-f8e188f9a63d), un ambiente de desarrollador diagonal administrador de paquetes diagonal distribución de Python, que incluye otras herramientas adicionales como *Jupiter Notebooks* y su más reciente actualización *Jupyter Lab*. Si bien no son ambientes integrados de desarrollo (IDE, integrated development enviroment) corren en un navegador y dentro de este incluyen las herramientas necesarias para programar.

Otro artículo que llamó mi atención, habla de [cómo crear un blog usando *HUGO*](https://theibbster.medium.com/how-to-build-a-blog-a-complete-beginners-guide-to-hugo-9f831b50aad). Para construir una página, este programa utiliza diversos archivos que se personalizan para administrar el contenido, mismo que escribe en [Markdown](https://www.genbeta.com/guia-de-inicio/que-es-markdown-para-que-sirve-y-como-usarlo). El blog mismo se crea en un repositorio en Github, que también es utilizado por muchos desarrolladores para guardar sus documentos, y se puede acceder a él mediante un administrador de dominios. Investigue diferentes alternativas para crear este blog, y me decidí por [Wowchemy](https://wowchemy.com/docs/getting-started/), que fácilmente me ayudo a crear esta página.

De hecho, cada que veo una publicación allí, deseo replicarla y aplicarla a mis propias bases de datos y a mis propios problemas. O crear nuevas bases de datos para aplicar grandes resultados que encuentro en twitter como hice [aquí](https://gonzalezhomar.netlify.app/post/mujeres2020/). De hecho, junto con TidyTuesday (que espero revisitar en otra publicación) son de las principales fuentes de inspiración para este blog.

## 4. Todo se conecta

En mi maestría programe unas pocas cosas en Python, pero nada grande. Luego leí el artículo de *The Atlantic*, y comentandolo con un amigo me recomendó que trabajara con Python y precisamente que utilizará la distribución Anaconda. Después la ví recomendada ampliamente en Medium. Demasiadas coincidencias como para no notarlas.

Además la parte de texto de las *notebooks* tanto de Google Colab, Jupyter y R, utilizan formato Markdown, mismo formato que el utilizado para crear blogs con *HUGO*. De hecho, Jupyter incluye entre sus opciones editar achivos exclusivos de Markdown y puede convertir archivos *notebooks* a archivos Markdown, conservando el contenido de dicha *notebook*. De esta manera, puedo reproducir pequeños proyectos en Jupyter... o grandes, convertirlos a Markdown, subirlos a mi Github y tengo una publicación. Como lo veo, todo se conecta.

![Matrix](matrix.png)