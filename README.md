# Scenery-Identificator
### Python AI image identification
#### Marco Antonio Camalich Pérez
## Selección del data set
#### Bansal, P. (2019). Intel Image Classification. Kaggle.com. https://www.kaggle.com/datasets/puneet6060/intel-image-classification?resource=download
El dataset utilizado en este proyecto fue obtenido de kaggle.com. Posee 24,335 fotografías divididas en tres subcarpetas: "prediction", "test" y "training". Estas fotografías pertenecen a una de seis diferentes subclases: 

{'buildings' -> 0,
'forest' -> 1,
'glacier' -> 2,
'mountain' -> 3,
'sea' -> 4,
'street' -> 5 }
‌
Hay alrededor de 14 mil imágenes en training, 3 mil en test y 7 mil en prediction (80/20 de proporción, solamente considerando training y test; excelente proporción para garantizar un entrenamiento suficiente para aprender patrones). Este dataset aprenderá las fotografías previamente procesadas mediante una red neuronal convolutiva para reconocerlas y clasificarlas en su debido subtipo.
## Preprocesado de los datos
Se realizó un algoritmo de aumentación de los datos sobre el grupo de testing de fotografías para mejorar la capacidad de generalización del modelo a crear. Esto se realiza al exponerlo a diferentes variaciones de los datos durante el entrenamiento, con distintas rotaciones, zoom y desplazamientos, aumentando la diversidad de los datos. Se realiza la impresión y el guardado de las imágenes generadas, lo que es fundamental para el entrenamiento eficiente de modelos de aprendizaje computacionales. Este procesamiento se encuentra sólido para futuros pasos, ya que se normalizaron los valores de los pixeles y se redujo la probabiblidad de memorización.
