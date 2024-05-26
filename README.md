# Scenery-Identificator
### Python AI image identification
#### Marco Antonio Camalich Pérez
## Descripción del Proyecto
El posterior repositorio contiene el desarrollo de un sistema de inteligencia artificial desarrollado en Python mediante la lógica de una red neuronal convolucional para identificar y clasificar diferentes tipos de fotografías de paisajes. Desde un edificio hasta un bosque, el presente programa aplicará el aprendizaje automático preprocesado de una variedad de imágenes de entrenamiento para hacer la posterior identificación de las imágenes de prueba.
## Selección del data set
#### Bansal, P. (2019). Intel Image Classification. Kaggle.com. https://www.kaggle.com/datasets/puneet6060/intel-image-classification?resource=download
El dataset utilizado en este proyecto fue obtenido de kaggle.com. Posee 24,335 fotografías en formato .jpg divididas en tres subcarpetas: "prediction", "test" y "training". Estas fotografías pertenecen a una de seis diferentes subclases: 

{'buildings' -> 0,
'forest' -> 1,
'glacier' -> 2,
'mountain' -> 3,
'sea' -> 4,
'street' -> 5 }
‌
Hay alrededor de 14 mil imágenes en training, 3 mil en test y 7 mil en prediction (80/20 de proporción, solamente considerando training y test; excelentes valores porcentuales para garantizar un entrenamiento suficiente para aprender patrones). Este dataset aprenderá las fotografías previamente procesadas mediante una red neuronal convolucional para reconocerlas y clasificarlas en su debido subtipo. La totalidad de las imágenes, incluyendo algunas de las preprocesadas mediante aumentación de los datos, se encuentran en el presente repositorio.
## Preprocesado de los datos
Se realizó un algoritmo de aumentación de los datos sobre el grupo de testing de fotografías para mejorar la capacidad de generalización del modelo a crear. Esto se realiza al exponerlo a diferentes variaciones de los datos durante el entrenamiento aumentando la diversidad de los datos. Algunas de las técnicas implementadas incluyen el reescalamiento de los píxeles, la rotación aleatorio de las imágenes, desplazamientos horizontales y verticales aleatorios, zoom, cambio en el ángulo de la fotografía, entre otros. Se realiza la impresión y el guardado de las imágenes generadas, lo que es fundamental para el entrenamiento eficiente de modelos de aprendizaje computacionales. Este procesamiento se encuentra sólido para futuros pasos, ya que se redujo la probabiblidad de memorización del modelo.
## Implementación de Modelo
### Elección de modelo: ResNet-50
#### Gao, H.-J., Liu, Z., Wang, C.-M., Liu, X., & Ren, J. (2020). Exploring the limits of ResNet50 on ImageNet. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. https://arxiv.org/abs/2004.11307
#### Dong, X., Lin, S., Cheng, G., Zhao, Y., Yang, L., & Zhang, X. (2021). Revisiting residual networks for image classification: A comprehensive study. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. https://arxiv.org/abs/2103.12793
Habiendo realizado el preprocesado pertinente de los datos, se determinó que el modelo ResNet-50 es una red neuronal convolucional profunda que ha demostrado un rendimiento sobresaliente en tareas de clasificación de imágenes, por lo que se convirtió en una opción idónea para el modelado del proyecto. La elección del modelo se basa en su capacidad para aprender características complejas de grupos variados de imágenes, y ha demostrado ser altamente eficiente en una amplia variedad de tareas de visión por computadora, lo que la convierte en una elección sólida para este identificador.
ResNet-50 se basa en una tecnología de autoaprendizaje basada en bloques residuales. Estos bloques permiten que las capas del modelo aprendan las diferencias entre las características de entrada y de salida en lugar de intentar aprender las características completas. Esto facilita el entrenamiento de redes muy profundas sin que las capas iniciales se vuelvan demasiado difíciles de entrenar. Las primeras capas del modelo pueden detectar bordes y formas simples en un grupo de imágenes aumentadas, mientras que las capas más profundas pueden detectar características abstractas. El potencial de este modelo es explotado con el aumento de épocas, ya que el modelo presente devuelve etiquetas en formato categórico y requiere una evaluación más exhaustiva y específica, es decir, cada imagen pertenece a una variedad de clases exclusivas, a diferencia del modo binario donde solo existen 2, por lo que se complica el estudio de la red.
En el ResNet-50 del presente repositorio, se utiliza un generador de datos para cargar las imágenes de entrenamiento y prueba desde los directorios correspondientes, con un tamaño de imagen de 150x150 píxeles y un tamaño de lote de 32 imágenes. La red neuronal se carga con los pesos preentrenados anteriormente de ImageNet, que es conjunto de datos de imágenes ampliamente utilizado en la investigación de visión por computadora. Ergo, esto significa que el modelo aprovecha el conocimiento previo adquirido al ser entrenado mediante un conjunto de imágenes generales masivo. Luego, se agregan capas adicionales al modelo para adaptarlo específicamente a la tarea de identificar y clasificar las fotos a los 6 diferentes tipos de paisajes identificados.
## Primera iteración del modelo
![image](https://github.com/CamalichM/Scenery-Identificator/assets/99758150/2d0e244c-c759-4908-8f1e-51e279e91f9f)
#### Gráfica de precisión del modelo
![image](https://github.com/CamalichM/Scenery-Identificator/assets/99758150/ff98d4c7-26e5-4831-a642-27fe500537ca)
#### Gráfica de pérdida del modelo
La primera iteración del modelo tuvo un total de 10 épocas que llevaron la exactitud del modelo a 0.7549 en una escala de 0 a 1, mientras que el loss tuvo un comportamiento de decremento exponencial contrario al aumento de la exactitud del modelo. Esto significa que el modelo fue mejorando gradualmente en su capacidad para hacer predicciones precisas, siendo capaz de clasificar correctamente aproximadamente el 75.49% de las imágenes de prueba. Al generar el contraste con las imágenes de prueba, se observó que el accuracy del modelo es de 0.53333 con un loss de 1.34, por lo que es un modelo considerablemente bueno pero tiene áreas de oportunidad para acercarse a una precisión casi perfecta.
El graficado de los resultados es sustentado por el escrito: 
#### He, K., Zhang, X., Ren, S., & Sun, J. (2015). Deep residual learning for image recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 770-778). Enlace: https://arxiv.org/abs/1512.03385
El paper determina el uso de gráficas de puntos para visualizar el error de entrenamiento y validación durante el entrenamiento de la red ResNet como un acercamiento adecuado y visualmente atractivo para una posterior toma de decisiones.. 

