# PRÁCTICA 1 THINKDSP

En esta práctica comenzaremos creando señales para entender sus propiedades. Conceptos de señales periódicas puras, complejas, visualización en el tiempo de las señales, visualización de la señal en el espectro, escuchar y digitalizar señales.

Herrameinta: Google Colab


## Comenzamos con la importación de la librería

```
import os

if not os.path.exists('thinkdsp.py'):
    !wget https://github.com/AllenDowney/ThinkDSP/raw/master/code/thinkdsp.py
    
```  
VAMOS A GENERAR UNA SEÑAL

Para generar una señal tenemos que utilizar o bien la función *cosSignal* o bien *sinSignal* que genera una señal periódica pura. La diferencia entre ambas es que una está desplazada sobre el eje del tiempo. Pero generan la misma señal pura.

Para generar una señal necesitamos configurar dos parámetros muy importantes:
* La frecuencia freq=440 significa que creamos una señal de 440Hz, si ponemos freq=1000 significa que creamos una señal de 1000Hz o 1KHZ (kiloHerzio).
* La amplitud amp=1.0 , sería el máximo volumen al que podemos escuchar ese sonido  o la potencia, o intensidad del sonido y 0 sería lo mínimo.

**Atención!!!** cos_sig --> Es donde se guarda dentro del ordenador la señal que genera, que lo guarda en memoria RAM del ordenador y a partir de este momento 
tenemos que utilizar esa nombre (variable) que se denomina cos_sig. Ese nombre es inventado, puedes inventarte el nombre que quieras para guardar la información en el
ordenador.

```
from thinkdsp import CosSignal, SinSignal

cos_sig = CosSignal(freq=440, amp=1.0, offset=0)

```

Para visualizarla necesitamos utilizar la función plot() que pinta la señal. 

**Nota:** decorate (xlabel = ' Tiempo (sg)') simplemente muestra en el eje X de la gráfica de la señal el texto: Tiempo (sg) para indicar que el eje X
muestra como se visualiza la señal en el tiempo.

```
from thinkdsp import decorate
cos_sig.plot()
decorate(xlabel = ' Tiempo (sg)')

```

### Ejercicios

1. Crea una señal sinSignal con una frecuencia de 880Hz y 1.0 de amplitud de señal. Pon el nombre de variable sin_sig
2. Dibuja y visualiza la nueva señal
3. Crea una señal grave de 100Hz otra señal de 1000Hz y otra señal de 3000Hz, utliza las variables grave, media y aguda para las tres señales
4. Visualiza las diferentes señales.
5. Crea otra señal de 880Hz de amplitud 2 cuyo nombre de variable sea sig_amp2


## SUMA DE SEÑALES, FORMA DE ONDA Y TIMBRE

Una señal pura tiene la forma de las señales anteriores tanto en el ejemplo como en los ejercicios. Porque son señales que contienen solo una frecuencia.

Si sumamos dos señales estamos creando una señal resultado de dos o más frencuencias, estas señales se denominan señales complejas y tienen la forma que váis a descubrir a continuación

copia este código que suma dos señales que hemos creado en el apartado anterior, para ellos simplemente hay que llamar al nombre de las variables donde hemos generado las señales y sumarlas como se muestra a continuación: Utilizamos una nueva variable que llamaremos suma_sig

```

suma_sig = sin_sig + cos_sig

```

### Ejercicio
1. Visualiza la señal resultado de la suma de las dos señales, es decir grafica suma_sig
2. ¿Cómo es su forma de onda? se parece a las dos originales. ¿Podemos viendo este tipo de señales intuir que está conformada de varias frecuencias y no son señales puras?
3. Suma las señales grave, medio, agudo y visualiza su resultado. suma_sig2


## GENERA EL SONIDO DE LAS SEÑALES

Ahora vas a aprender mediante el código Python y ThinkDSP a crear el sonido de las señales que has creado, para ello necesitamos utilizar una serie de funciones que digitalizan la señal a una señal discreta o digital. Aunque no lo vamos a ver en este tema, a esto se le denomina *muestreo* de la señal original para crear una señal digital y poder procesarla en el ordenador. Los paramétros que son
* duration = 0.5 indica el tiempo en segundos que vamos a crear
* start=0 desde que punto empieza, en concreto, desde el comienzo
* framerate indica la calidad digital cuanto mayor sea el número será una señal que sonorá mejor. con 11025 será suficiente.

Y utilizaremos la función Audio para poder escuchar esa señal digitalizada 

Crea un bloque de código y copia el siguiente código:

```
wave = sin_sig.make_wave (duration=0.5, start=0, framerate=11025)

from Ipython.display import Audio
audio = Audio (data=wave.ys, rate=wave.framerate)
audio

```

### Ejercicios

1. Crea el sonido de todas las funciones que hemos creado desde el principio de la práctica tanto las señales puras como las señales creadas de la suma de varias señales puras. TOTAL de 8 señales
cos_sig, sin_sig, grave, medio, bajo, sig_amp2, suma_sig, suma_sig2

2. Y explica la diferencia que escuchas en cada una de ellas.
