# Procesamiento-de-la-lengua-de-signos-LSE-
 
Procesamiento de la lengua de signos española mediante aprendizaje automático. Este trabajo presenta el código relacionado con mi Trabajo Fin de Grado de la carrera en Ingeniería en Sistemas Audiovisuales en la Universidad Pompeu Fabra.

En estos códigos se han creado diferentes modelos de aprendizaje para procesar las diferentes palabras o letras del lenguaje de signos español. Para ello, he trabajado con tres conjuntos de datos diferentes. El primero es un conjunto de datos abierto disponible en, https://www.kaggle.com/datasets/rub3ntercero/lenguaje-de-signos-espaol, pero los otros dos con los que he trabajado no son conjuntos de datos abiertos.

Primero, explicaré las versiones de las librerías que he utilizado para ejecutar el programa, y luego haré una breve descripción y explicación de cómo funciona cada script que he usado.

Las librerias y sus versiones que se han utilizado en este trabajo:
- Python: 3.11.0
- cv2: 4.9.0
- numpy: 1.26.4
- tensorflow: 2.16.1
- PIL: 10.3.0
- imageio: 2.34.0
- matplotlib: 3.8.4
- sklearn: 1.4.1.post1
- keras: 3.1.1

# Frames
Este script convierte los videos en fragmentos. Para ello, aplica diferentes funciones para capturar únicamente los frames necesarios que permitan seguir correctamente el movimiento reflejado en el video. Las variables se pueden modificar dependiendo del video de entrada y del resultado que se quiera obtener.

# Openpose
En este script hay dos apartados. El primero une los puntos JSON obtenidos con OpenPose para que el resultado sea visible y la estructura una correctamente los puntos de las manos, cara y cuerpo. Para la creación de los archivos JSON que contienen los puntos clave, se han seguido los pasos explicados en https://github.com/CMU-Perceptual-Computing-Lab/openpose. 
El segundo apartado se utiliza para el conjunto de datos de Kaggle. En este, se usa el archivo hand_pose_model.pth descargado desde internet, que es capaz de encontrar los 21 puntos clave en las manos. Se puede ver en el código el paso a paso de cómo se realiza.

# Alfabeto
En este archivo, se realiza una clasificación del conjunto de datos de Kaggle. Para ello, se utilizan diferentes métodos, empezando por una CNN y luego probando con diferentes modelos preentrenados que ayudan a generalizar y precisar el modelo.

# LSE - LSTM
En este archivo, se realiza la clasificación de todas las palabras del alfabeto, tanto dinámicas como estáticas, basándose en una secuencia de fotos que distingue las letras hechas con la mano derecha y con la izquierda. Este conjunto de datos no es público, por lo que no puedo proporcionar el enlace. Para la clasificación, primero creamos y aseguramos que las secuencias estén bien etiquetadas, y luego entrenamos el modelo utilizando un LSTM.

# DILSE-ARASAC
Este script también contiene un clasificador LSTM, pero en este caso, se da mucha importancia a las técnicas de aumento de datos (data augmentation), ya que este conjunto de datos (no público) no contiene suficientes imágenes para entrenar correctamente un modelo LSTM.

