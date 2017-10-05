---
layout: post
title: Clasificando las plantas del patio
---

El proyecto de clasificación de imágenes en el que trabajaba para una universidad local está _"on hold"_ por el momento, así que me di el tiempo para escribir algo sencillo de clasificación de las plantas en mi patio. **Spoiler alert: Sigo sin saber qué plantas existen en mi patio** .

La idea surgió porque no me he interesado por la botánica así que honestamente no sé nada de plantas, ni cómo se llaman, ni cuando dan frutos, en fin, si veo un árbol y no veo frutas, automáticamente asumo que es de [mango](https://es.wikipedia.org/wiki/Mangifera). ¿Pero cómo podrías confundirlos dirían algunos, especialmente mi mamá? Si las hojas son alargadas y más ancha por en medio, es definitivamente mango, pero si son redondas y medianas entonces son de [aguacate](https://es.wikipedia.org/wiki/Persea_americana) y así sucesivamente.

Entonces si clasifico correctamente las hojas, podré saber entonces las plantas. No es mala idea, de hecho decidí "entrenar" un _neural network_ que hiciera el trabajo por mí.

## Utilizando CNTK o TF

Hace un año dejé de escribir modelos completos de _neural networks_ y en el campo de _AI_ y _ML_, 12 meses es una eternidad, para muestra el _framework_ que utilicé para mi tesis, [Theano](http://deeplearning.net/software/theano/index.html), será [descontinuado](https://groups.google.com/forum/#!topic/theano-users/7Poq8BZutbY). La razón es justa y necesaria, básicamente es demasiado trabjo mantener el proyecto cuando ya existen otros _frameworks_ que son desarrollados o soportados por "The Big Four": Google (Tensorflow), Microsoft (CNTK), Facebook (Torch/Caffe2/Pytorch) y Amazon (MXNET) y otros más.

Entonces para empezar a escribir modelos y aplicar cosas nuevas, que realmente no es del todo necesario,  viene el dilema de decidir en cuál _framework_ escribirlos. Así que decidí optar por... **CNTK** ([CogNitive ToolKit](https://www.microsoft.com/en-us/cognitive-toolkit/))

_Vamo a usar CNTK_, por dos razones:
1.- Nunca antes lo he usado, así que estaría bien aprender.
2.- En MCITCSA usamos C# y Microsoft _Frameworks_ para desarrollo, así *mato a dos pájaros de un tiro* y leo más sobre como sacar provecho a *machine learning* para la empresa sin alterar demasiado el flujo de trabajo. La misma razón por la que escogimos **F#** para [lenguaje funcional]({% post_url 2017-08-16-new-horizon %}).

## Recolectando piezas 
### La Data
Ahora, ¿con qué materia prima voy a entrenar una _Neural Net_? Podría tomar fotos de todas las hojas de plantas diferentes que hay en mi patio, y en los patios de la oficina, los vecinos, mi Tía (que es dueña de una finca), mi hermana y así _ad infitimun_, además de clasificarlas. Perooooo... estamos en 2017 y es probable que el código ya esté en github o bitbucket.

Así que encontré un dataset para clasificación de [enfermedades en las plantas (_plant disease clasification_)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5032846/) que efectivamente está en github, gracias a [Mohanty S.](https://github.com/salathegroup/plantvillage_deeplearning_paper_dataset). Al principio me costó entender el porqué tantas imágenes repetidos, y con diferentes colorización pero después de leer el paper hay una razón, la comparación de _Deep Learning_ con métodos más establecidos, en este caso _Support Vector Machines_ y comparación de certeza entre imágenes de color, blanco & negro y segmentadas.

### El modelo
Una vez colectada la data (ya sé que son datos en español, pero data me gusta más), me tocó escoger el modelo. En mi tesis utilizamos _Feed forward Neural Networks_, que tienen detalles para escalar en problemas más grandes (data y parámetros), y dado que es una tarea de clasificación de imágenes me decidí por utilizar una [_Convolutional Neural Network (CNN)_](https://github.com/Microsoft/CNTK/blob/v2.1/Tutorials/CNTK_103D_MNIST_ConvolutionalNeuralNetwork.ipynb) y así de paso aprender más sobre esta estructura.
 
Y vaya que el campo ha explotado, ahora existen Fast-CNN, R-CNN, HyperNetworks y paro de mencionar porque siguen creciendo los diversos tipos de modelos (lo mismo sucede con [GANs](https://github.com/hindupuravinash/the-gan-zoo)). Entonces por cuestiones de practicidad, decidí utilizar el modelo que viene en los tutoriales de CNTK para [clasificación de imágenes con _CNNs_](https://github.com/Microsoft/CNTK/blob/v2.1/Tutorials/CNTK_103D_MNIST_ConvolutionalNeuralNetwork.ipynb).

El modelo inicial, en el paquete de principiante, es una [ResNet (Residual Networks)](https://arxiv.org/pdf/1512.03385v1.pdf) de 18 capas; la ventaja principal de las _ResNets_ es que reciben entradas de la imagen original o de capas anteriores en las capas más profundas, uno se salta capas básicamente. Si les interesa más les recomiendo ampliamente leer el artículo, la intuición detrás es sencilla.

Además de utilizar en un modelo ya existente, decidí por utilizar _transfer learning_, es decir, los parámetros ya calculados y sobre esos _"aprender"_ la última capa, la que hace la asignación del _label_ a la imagen. La decisión la tomé después de comparar el entrenamiento de todo el modelo, es decir _"aprendiendo"_ todos los parámetros y entrenar solamente la última capa (_transfer learning). Al final el _accuracy_ de _full training_ era ~2% mejor que _transfer learning_ pero el tiempo de entrenamiento era 4x veces mayor. 

### Lo Experimento

Durante la clasificación, el _accuracy_ en tiempo de prueba (_testing_) se queda estancado en ~94%, un gran margen de diferencia en comparación a los resultados obtenidos por [Mohanty et. al](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5032846/). Una de las razones principales es la diferencia en los modelos, ellos utilizaron: [**Google LeNet Inception V3**](https://arxiv.org/abs/1512.00567), una _CNN_ con cerca de 50 capas y una estructura interna por capas un tanto diferente, a la ResNet que estaba usando.

Entonces... Podría usar **Inception V3** que ya existe como [modelo en CNTK](https://github.com/Microsoft/CNTK/tree/master/Examples/Image/Classification/GoogLeNet/InceptionV3), pero solamente existe como modelo hecho en BrainScript. So, ¿qué hice? Descargué los modelos en python con la mayor cantidad de capas disponibles, así fue como terminé con una [_ResNet-50_](https://github.com/Microsoft/CNTK/blob/master/PretrainedModels/Image.md#resnet), una Residual Network con 50 capas. Que, para ser sinceros, está muy por debajo de las 152 capas que fueron utilizadas en los experimentos de Microsoft, pero hey! ¿Quién tiene 8 GPUs en clúster listos para ser utilizados? Not this guy!

Ahora sí, ya con un modelo lo suficientemente robusto, vamos a _"aprender"_. El 98% de _accuracy_ en tiempo de prueba que estaba esperando por fin se materializó. Como nota: Al ser un modelo relativamente grande y usando _transfer learning_ muchas _epochs_ resultan en _overfitting_, entonces como recomendación: ~13 epochs es más que suficiente.

### Prueba de fuego (Plantas en mi patio)

Ya con el modelo armado y entrenado, vamos a clasificar las plantas en mi patio. 

![Hoja de chile](/img/backyard/leaf_chile_back.jpg )
![Hoja de limón](/img/backyard/leaf_sick.jpg )
![Hojas varias](/img/backyard/hojas_varias.jpg )

Después de todo, tengo al parecer plantas de:
-  Mora saludable (planta desconocida)
- tomate con tizón tardío (chile con enfermedad)
- maíz saludable (limón)

Era de esperarse que ninguna de las fotos de las plantas que tomé fueran clasificadas correctamente, porque simplemente no existen en la data inicial, es decir el modelo nunca _"aprendió"_ que existen hojas de limón, chile o lo que sea que es lo otra planta. Aún así, hizo un buen trabajo en cuanto le muestro una hoja de una planta que _"aprendió"_. Algo así como la mayoría de los alumnos en primaria de este país.

![Cereza con moho](/img/backyard/cherry_leaf_pwmdew.jpg)

### ¿Es mejor utilizar CNTK vs TensorFlow?
 No sé, si fuera por modelos y actividades en github, TF es definitivamente la mejor opción, cada vez que leo una técnica nueva que es bastante prometedora por lo general ya existe alguna variación del algoritmo en tensorflow. Por el otro lado, si ya tienen un flujo de trabajo establecido con MSFT, realmente aprender CNTK no es una mala decisión.

Así que el criterio, depende de varios factores que son especiales en cada caso de uso.

## Takeaways

Al final, el ejercicio me sirvió para actualizarme un poco en cuanto a la ingeniería de _Neural Nets_, me ayudó a ver cómo está el campo de _CNNs_, también pude aplicar nuevos conocimientos del curso #3 de Andrew Ng en Coursera.

Los resultados al final no fueron exactamente lo mejor, pero en cuestión de experiencia todo el mini-proyecto valió la pena.