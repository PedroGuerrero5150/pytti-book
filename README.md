# Nota preliminar
Desarrollada por Katherine Crowson, Henry Rachootin y David Marxs [PyTTI] PyTTI-Tools es una versión gratuita del código original Rachootin entendida para usuarios de alto nivel. Herramientas como esta se han hecho muy populares entre creadores de contenido debido a su impresionante poder generativo y la relativa facilidad con la que este es accesible. 
A continuación describiré los pasos que tomé para realizarla. 
[link a la obra](https://drive.google.com/drive/folders/1kHNs5WzcNBBdhpUHJ-oCyezSt5PKqH6D?usp=sharing)  

## Metodología

**Google Colab**
El código se corrió en la plataforma de Google Colab debido a la necesidad (propia de la gran mayoría de arquitecturas de Deep Learning) de GPUs. También se puede usar una máquina local que los tenga, pero ese no era mi caso y probablemente también lo sea el de gran parte del público objetivo.
Google Colab permite conectarse a GPUs de forma remota para correr el código de manera gratuita, pero debido a las limitaciones que la versión gratuita trae con sigo -GPUs inferiores y frecuentes interrupciones durante el proceso- es recomendable suscribirse a la membresía “pro”. Antes de conectarse a la máquina remota, se debe cambiar el apartado de “Hardware accelerator” de CPU a GPU.

**Paso 1: Conectar ejecución a Google Drive**
Paso opcional, pero recomendado: El video se generó a partir de cientos de imágenes individuales, además que los modelos pre enredados pueden llegar a pesar mucho. Correr la celda 1.1 y hacer click en la casilla “mount_gdrive” para que las carpetas necesarias sean creadas con los nombres predeterminados y la ejecución sea fluida. 

**Paso 1.3: Instalar todo los demás**
Correr esta celda para instalar las dependencias: módulos y bibliotecas usadas en la implementación. 

**Paso 2: Configurar experimento**
En este punto cabe mencionar que estamos trabajando -en su vasta mayoría- con modelos pre entrenados (VQ-GAN con imagenet.ckpt, Autoencoder convgg.pth) y por ende con entrenamientos no parametrizables (recordemos que el notebook pretende ser usado por usuarios de alto nivel) por lo que en este apartado, las variables llamadas “Prompt Settings” son en realidad donde el usuario puede explotar su imaginación y creatividad. 


**Prompt Setttings**
Aquí se describen las escenas a generar. Estas deben separarse por | y además pueden llevar un peso (especificado después de los dos puntos) que, dependiendo de su valor (positivo o negativo) estará más o menos  presente en la obra. 
Los autores recomiendan prácticas como tomar en cuenta cuando fue entrenado el modelo para no tener errores de tipo introducir una película que se hizo pública en el 2022 a un modelo que se entrenó en 2020.  También se recomienda el uso de fuentes de imágenes en la web. Yo por ejemplo, especifiqué un sitio de un artista para que el estilo de este sea imitado: artstation art by Azat Nurgaleev.
Los valores que introduje en este apartado fueron:

scenes: eternal feminine | big translucent women eyes | rivers of wine

scene_suffix\: | satellite image:-1:-.95 | text:\-1:-.95 | watermark\:\-\1\:-.95 | backyard telescope\:\-\1\:-.95 | map\:\-\1\:-.95

scene_prefix: astrophotography #pixelart | artstation art by Azat Nurgaleev | #conceptart eternal feminine |  

**Otros parámetros configurados**
A continuación, los demás parámetros que se configuraron que -si bien no tienen voz sobre los elementos protagonistas que aparecerán en la obra- sí pueden determinar rasgos estéticos de ella.

| Parámetro   | Descripción | Valor introducido |
| ------------- | ------------- | ------------- |
| steps_per_scene  | Total number of steps to spend rendering each scene | 60100 |
| image_model  | Select how your image will be represented | vqgan |
| pre_animation_steps | Number of steps to run before animation starts, to begin with a stable image | 100 |
| sampling_mode | How pixels are sampled during animation | bicubic |
| animation_mode | Select animation mode or disable animation | 3D |
| translate_x | Horizontal image motion as a function of time in seconds. | -1700\*sin(radians(1.5)) |
| translate_z_3d | Forward image motion as a function of time in seconds | (50+10\*t)\*sin(t/10\*pi)\*\*2 |
| rotate_3d | Image rotation as a quaternion  as a function of time  in seconds | \[cos(radians(1.5)), 0, -sin(radians(1.5))/sqrt(2), sin(radians(1.5))/sqrt(2)\] |


Tabla 1. Otros parámetros configurados para la realización de la obra artística. 
Ejecutar las 19 celdas de este apartado una vez configurados los parámetros descritos.

**Paso 2.3: Ejecución** 
Posteriormente se debe correr la celda 2.3 para generar las imágenes. Fue a esta altura donde me topé con mi primer problema: Al correr la celda saltaba el error “pytti_test\AdaBins\pretrained\archive file not found” lo cual fue resuelto -después de algo de indagación- descargando el modelo pre entrenado de Adaptive Bins y descomprimiendolo en la carpeta con esa dirección en Drive. Así mismo, dejaré el link para [descargar el modelo](https://drive.google.com/file/d/1XdMsUUPIp4-JQP2x20wQZXPGJizSN9ZO/view?usp=sharing) si alguien se topa con el mismo inconveniente.  
Una vez resuelto el problema, las imágenes son generadas e impresas cada 50 unidades en pantalla, guardándose en la carpeta “images_out” del directorio creado por el código.

**Paso 3: Reenderización del video**
Correr la celda 3 debería renderizar el video a generar en función de las imágenes en la carpeta “images_out”, pero cuando yo lo hice esto no ocurrió. Habiendo ya generado las imágenes el problema no era crítico, por lo que utilicé la parte del código de Henry Rachootin “pytti 5 beta” que renderiza los videos para hacerlo. Este código no lo compartiré siendo este una fuente de ingreso del programador al ser exclusivo para usuarios que han pagado por él, pero debo recalcar que este -teniendo ya la imágenes en la carpeta- es un problema relativamente trivial y su solución puede venir de la mano de un código simple generado por un individuo o de un software auxiliar. 



# PyTTI-Tools Documentation and Tutorials

[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://pytti-tools.github.io/pytti-book/intro.html)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pytti-tools/pytti-notebook/blob/main/pyttitools-PYTTI.ipynb)
[![DOI](https://zenodo.org/badge/461043039.svg)](https://zenodo.org/badge/latestdoi/461043039)
[![DOI](https://zenodo.org/badge/452409075.svg)](https://zenodo.org/badge/latestdoi/452409075)


## Requirements

    pip install jupyter-book
    pip install ghp-import

## Building and publishing

    # Add a new document to the book
    git add NewArticle.ipynb
    
    # The page won't show up unless you specify where it goes in the TOC
    git add _toc.yml
    git commit -am "Added NewArticle.ipynb"
    jupyter-book build .
    ghp-import -n -p -f _build/html
