


1. Introducción

En este proyecto se presenta la implementación de redes neuronales entrenadas para la mejora de resolución de vídeos e imágenes principalmente, el proyecto consiste en el entendimiento y mejora del proyecto ESRGAN que se basa en el desarrollo original SRGAN.

La Red Adversaria Generativa de Superresolución (SRGAN) es un trabajo fundamental que es capaz de generar texturas realistas durante la superresolución de una sola imagen. Sin embargo, los detalles alucinados suelen ir acompañados de artefactos desagradables. Para mejorar aún más la calidad visual, estudiamos a fondo tres componentes clave de SRGAN: arquitectura de red, pérdida de confrontación y pérdida de percepción, y mejoramos cada uno de ellos para derivar un SRGAN mejorado . En particular, presentamos el bloque denso residual en residual (RRDB) sin normalización por lotes como la unidad básica de construcción de la red. Además, tomamos prestada la idea de GAN relativista para permitir que el discriminador prediga la realidad relativa en lugar del valor absoluto. Finalmente, mejoramos la pérdida de percepción utilizando las características antes de la activación, lo que podría proporcionar una supervisión más fuerte para la consistencia del brillo y la recuperación de la textura. Beneficiándose de estas mejoras, el ESRGAN propuesto logra consistentemente una mejor calidad visual con texturas más realistas y naturales que SRGAN y ganó el primer lugar en el PIRM2018-SR Challeng

1. Explicación reescalado bilineal

Es una técnica de escalado que simplemente escala los pixeles existentes con un multiplicador en forma de número integro.

Este escalado usa un algoritmo de interpolación del tipo &quot;Nearest Neighbor&quot;, también denominado de interpolación proximal, y permite introducir la información que falta debido a la redimensión de la imagen partiendo de la información original, colocando el color asociado al pixel original más cercano al pixel objetivo.

<img width="871" alt="image31" src="https://user-images.githubusercontent.com/82851310/119289420-2fa87580-bc10-11eb-96db-3b980fca0e1b.png">
<img width="830" alt="image32" src="https://user-images.githubusercontent.com/82851310/119289423-30d9a280-bc10-11eb-9870-542b18541e06.png">


1. Explicación redes neuronales

Las redes neuronales artificiales son un modelo inspirado en el funcionamiento del cerebro humano. Está formado por un conjunto de nodos conocidos como neuronas artificiales que están conectadas y transmiten señales entre sí. Estas señales se transmiten desde la entrada hasta generar una salida.

Cada una de las neuronas de la red posee a su vez un peso, un valor numérico, con el que modifica la entrada recibida. Los nuevos valores obtenidos salen de las neuronas y continúan su camino por la red. Este funcionamiento puede observarse de forma esquemática en la siguiente imagen.

Una vez que se ha alcanzado el final de la red se obtiene una salida que será la predicción calculada por la red. Cuantas más capas posea la red y más compleja sea, también serán más [complejas las funciones](https://www.atriainnovation.com/vision-artificial-industrial/) que pueda realizar

Para conseguir que una red neuronal realice las funciones deseadas, es necesario entrenarla. El entrenamiento de una red neuronal se realiza modificando los pesos de sus neuronas para que consiga extraer los resultados deseados.




Mejoras del SRGAN

Adopte un modelo más profundo utilizando Residual-in-Residual Dense Block (RRDB) sin capas de normalización por lotes.

emplee GAN promedio relativista en lugar del GAN de vainilla.

mejorar la pérdida de percepción utilizando las funciones antes de la activación.

A diferencia de SRGAN, que afirmó que los modelos más profundos son cada vez más difíciles de entrenar, nuestro modelo ESRGAN más profundo muestra su rendimiento superior con un entrenamiento sencillo.

![image6](https://user-images.githubusercontent.com/82851310/119289515-59619c80-bc10-11eb-86b9-43790762515c.png)
![image7](https://user-images.githubusercontent.com/82851310/119289518-5a92c980-bc10-11eb-9ddc-f3dc2bb70064.png)


Se propone la estrategia de interpolación de redes para equilibrar la calidad visual y la PSNR esta estrategia de interpolación de la red proporciona un control fluido del modelo RRDB\_PSNR y el modelo ESRGAN ajustado.

![image8](https://user-images.githubusercontent.com/82851310/119289541-68e0e580-bc10-11eb-9f02-d8b1c5a629b1.png)

Comparaciones visuales generales para mostrar los efectos de cada componente en ESRGAN. Cada columna representa un modelo con sus configuraciones en la parte superior. El signo rojo indica la principal mejora en comparación con el modelo anterior.

![image10](https://user-images.githubusercontent.com/82851310/119289570-7c8c4c00-bc10-11eb-9905-7dded67a0b9b.png)


1. Explicación del funcionamiento del programa

- Primero corremos el programa con en link de Github, opcionalmente podemos agregar nuevos modelos pre entrenados si así lo deseamos.

- A continuación, cargamos las imágenes a Google Colab, las cuales se guardarán en la carpeta LR.

- Es importante verificar que las carpetas se encuentren vacías, ya que si no, las imágenes no se podrán cargar correctamente en dichas direcciones.

![image11](https://user-images.githubusercontent.com/82851310/119289559-74cca780-bc10-11eb-93aa-31530da19ea5.png)


En esta celda se muestra el código para cargar las imágenes,El widget de carga solo está disponible cuando la celda se ha ejecutado en la sesión actual del navegador. Vuelva a ejecutar esta celda para habilitarla.

![image12](https://user-images.githubusercontent.com/82851310/119289585-831ac380-bc10-11eb-8eb4-1e4e4be8f698.png)


Agregamos los videos el nombre de archivo de vídeo no debe contener espacios.
![image13](https://user-images.githubusercontent.com/82851310/119289603-86ae4a80-bc10-11eb-81cd-b2258ec60558.png)


Esta celda convierte su video en cuadros individuales y los guarda en la carpeta &#39;LR&#39;.

![image14](https://user-images.githubusercontent.com/82851310/119289611-88780e00-bc10-11eb-8f58-a8f2f4579cee.png)


En esta sección se agregan los modelos pre entrenados.


![image15](https://user-images.githubusercontent.com/82851310/119289622-8ca42b80-bc10-11eb-8717-e9ccb9edc2cd.png)


En esta sección se selecciona el modelo pre entrenado con el cual se va a ejecutar el programa y también se selecciona la plataforma de ejecución
![image15](https://user-images.githubusercontent.com/82851310/119289634-9037b280-bc10-11eb-80c5-915807e3cc08.png)


En esta celda se ejecuta para codificar los resultados en un video.

![image16](https://user-images.githubusercontent.com/82851310/119289641-9332a300-bc10-11eb-9772-b0fea87171e0.png)


1. Implementación

- El programa fue implementado en la terminal de comandos Windows, la tarjeta gráfica y la memoria RAM que utilizamos fue la de nuestro propio equipo aunque a que tuvimos dificultades lo implementamos en nuestro equipo con éxito

- Sin embargo para obtener mejoras en velocidad de procesamiento y tarjeta gráfica el proyecto también fue implementado en Google Colab, donde la restricción de nuestro tamaño de dataset no fue un problema.

- En nuestro equipo inicialmente debemos ingresar la fotografía en formato png a la carpeta LR (low resolution) y posteriormente ingresamos a la ventana de comandos de Windows, abrimos la dirección del proyecto y corremos el archivo &quot;test.py&quot;.

- Posteriormente el programa toma tiempo en realizar el escalamiento y la imagen es guardada en la carpeta Result.

1. Resultados de la implementación

A continuación se muestran algunos resultados de la primera implementación del código, cabe mencionar que algunos no fueron muy buenos debido a que la imagen inicial fue con extrema mala resolución y tamaño excesivamente pequeño, esto se realizó para poner a prueba la efectividad del programa.

![image18](https://user-images.githubusercontent.com/82851310/119289651-97f75700-bc10-11eb-9d46-cb95554be263.png)


En las siguientes imágenes se aprecia el resultado del mismo escalado, con un poco de zoom podremos observar algunos defectos, sin embargo a distancia el resultado es muy aceptable, claramente esta imagen es muy pequeña 120x120 por lo que al acercar la imagen se clarifican las diferencias. ![image19](https://user-images.githubusercontent.com/82851310/119289661-9c237480-bc10-11eb-9f9e-2725f2c80e8d.png)


![](RackMultipart20210524-4-1s73ajx_html_ae988b1ce44b354b.png)

Las próxima imágen es de buena resolución pero de bajo tamaño, la primera es de 200 x 200 píxeles, posteriormente al reescalado se obtuvo una imagen de 800 x 800 píxeles, se puede apreciar que la calidad es mayor.

![image20](https://user-images.githubusercontent.com/82851310/119289674-a5144600-bc10-11eb-9124-1d9868671543.png)


La imagen se escaló de 5000x200 a 20000x800, sin embargo la diferencia no fue muy notable debido a que la imagen inicial es de alta resolución, a pesar de ello se aprecia una mejor calidad de imagen.

![image21](https://user-images.githubusercontent.com/82851310/119289679-a776a000-bc10-11eb-86fb-7938130511a5.png)


\* En este caso el reescalado fue bueno ya que la calidad de imagen inicial es alta aunque muy pequeña.

La calidad de las imágenes dependerá de si la imagen original tenía una buena calidad. Algunas fotografías aumentaron considerablemente de calidad al aumentar su resolución, pero para poder mejorar aún más es necesario hacer una serie de implementaciones más.

También podremos analizar el progreso con algunos videos; lo que podemos hacer es subir un video de corta duración con una resolución menor a la esperada (el video tiene que ser de corta duración, debido al problema de procesamiento y a su tiempo de respuesta).

Posterior a subir el video, debemos convertirlo en frames individuales, y con esto generar muchos png, los cuales son procesados después como frames individuales.

Podemos reagrupar los muchos frames obtenidos, o en su defecto, dejarlos como frames individuales (png).

Al final de compilarlo, y reagrupar las imágenes para hacerlo un video, como estaba en su inicio, obtuvimos estos resultados:

![image22](https://user-images.githubusercontent.com/82851310/119289689-acd3ea80-bc10-11eb-8849-1c69e0a66301.png)


- Como podemos observar, el video pasó de una baja resolución, a una resolución mayor.

1. Mejoras

Al realizar el procedimiento de escalamiento dos veces logramos un doble escalamiento y por lo tanto una mejora, sin embargo la capacidad de procesamiento de la computadora debe ser alta para que el programa no tenga dificultades respecto a la memoria RAM. Implementando el programa con una tarjeta gráfica de las que se muestran a continuación, se obtiene una calidad de imagen más alta otra mejora importante es la cantidad de elementos que contiene el dataset, en este caso se implementaron varios para incrementar la calidad de las imágenes, esto nos permite mejorar el entrenamiento de la red neuronal y con ello tendremos mayor precisión en los resultados.

**Quadro Series:**

Quadro GV100, Quadro GP100, Quadro P6000, Quadro P5000, Quadro P4000, Quadro P2000, Quadro P1000, Quadro P620, Quadro P600, Quadro P400, Quadro M6000 24GB, Quadro M6000, Quadro M5000, Quadro M4000, Quadro M2000, Quadro K6000, Quadro K5200, Quadro K5000, Quadro K4000, Quadro K4200, Quadro K2200, Quadro K2000, Quadro K2000D, Quadro K1200, Quadro K620, Quadro K600, Quadro K420, Quadro 410

**Quadro Blade/Embedded Series :**

Quadro P5000, Quadro P3000, Quadro M5000 SE, Quadro M3000 SE, Quadro K3100M

**Quadro NVS Series:**

NVS 810, NVS 510, NVS 315, NVS 310

**Quadro Sync Series:**

Quadro Sync II, Quadro Sync

**NVS Series:**

NVS 810, NVS 510, NVS 315, NVS 310

A continuación se muestran los modelos extras que se agregaron para incrementar la calidad de salida de las imágenes, con ello las redes neuronales cuentan con mayor información para poder realizar las predicciones.
![image23](https://user-images.githubusercontent.com/82851310/119289697-b1989e80-bc10-11eb-966d-9586946699e0.png)


En las siguientes imágenes se muestra el doble reescalado con la obtención de mejores resultados, la aplicación de una mejora en el dataset sin duda ayuda al modelo a obtener mejores resultados, aunado a esto la plataforma CUDA es más potente que la de nuestro como podemos observar a continuación, la calidad de la imagen es mucho mayor en el escalado final.

<img width="915" alt="image24" src="https://user-images.githubusercontent.com/82851310/119289708-b78e7f80-bc10-11eb-9c1b-ee5f581d7601.png">


En este caso se muestra una imagen .jpg que se convirtió a .png para poderla ingresar en el programa, el escalado fue de 936 x 688 a 3744 x 2752, por lo que se obtuvo una mejora muy significativa que podemos apreciar a continuación.
<img width="958" alt="image28" src="https://user-images.githubusercontent.com/82851310/119289730-beb58d80-bc10-11eb-9e0e-c00a73ed8aee.png">



A continuación podemos observar distintas ejecuciones donde podemos comparar los resultados de nuestro equipo con el mismo modelo de entrenamiento contra los resultados de Google colab y CUDA

Imagen original

![image33](https://user-images.githubusercontent.com/82851310/119289739-c412d800-bc10-11eb-944d-9a268baf3d3e.png)


Ejecución en CPU DELL Core i7 8Gb RAM Intel HD Graphics 400 NVIDIA NVS 5200M

![image34](https://user-images.githubusercontent.com/82851310/119289744-c6753200-bc10-11eb-9536-bc650fe7d48d.png)


Ejecución con Google colab NVIDIA-SMI 465.19.01 y CUDA 11.2 , modelo RRDB\_ESRGAN\_x4

![image35](https://user-images.githubusercontent.com/82851310/119289751-c83ef580-bc10-11eb-9568-abe22095f334.png)


1. Conclusión y comentarios

Gracias a la implementación de redes neuronales es posible lograr ciertas aplicaciones que de manera normal serían muy complicadas y tardadas.

En conclusión, es posible lograr implementar un programa que mejore la calidad de videos e imágenes gracias al uso de machine learning. El tiempo que tardará en renderizar dependerá de la capacidad de procesamiento de la máquina en la cual se esté trabajando.

## **Bibliografía**

[https://www.youtube.com/watch?v=S487S0FQm0w](https://www.youtube.com/watch?v=S487S0FQm0w)

[https://www.youtube.com/watch?v=2ZwYjY4\_Wj0](https://www.youtube.com/watch?v=2ZwYjY4_Wj0)

[https://www.geeknetic.es/Guia/1662/Integer-Scaling-Que-es-y-como-funciona.html](https://www.geeknetic.es/Guia/1662/Integer-Scaling-Que-es-y-como-funciona.html)

[https://www.atriainnovation.com/que-son-las-redes-neuronales-y-sus-funciones/#:~:text=Las%20redes%20neuronales%20artificiales%20son,entrada%20hasta%20generar%20una%20salida](https://www.atriainnovation.com/que-son-las-redes-neuronales-y-sus-funciones/#:~:text=Las%20redes%20neuronales%20artificiales%20son,entrada%20hasta%20generar%20una%20salida).
