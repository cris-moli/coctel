#  Fiesta de Cóctel
 ## Introducción
En este trabajo desarrollaremos la práctica de “la fiesta de cóctel”, esta consiste en grabar diferentes conversaciones desde diferentes micrófonos en una reunión, en nuestro caso hicimos uso de la aplicación grabadora de voz desde los celulares, en un cuarto insonoro a una distancia de aproximadamente 2 metros cada uno de los micrófonos que se encontraban en un punto central, esto permitió la captura de tres audios guardados desde tres diferentes celulares de aproximadamente 15 segundos cada audio. 
## Tranformada rápida de Fourier
La Transformación rápida de Fourier, FFT para abreviar, es un importante método de medición en la tecnología de medición de audio y acústica. Descompone una señal en sus componentes espectrales individuales y así proporciona información sobre su composición. Los FFT se utilizan para el análisis de errores, el control de calidad y la monitorización de las condiciones de las máquinas o sistemas. 
## ¿Qué es ICA?
El análisis de componentes independientes es un método probabilístico para aprender una transformación lineal de un vector aleatorio. El objetivo es encontrar componentes que sean máximamente independientes y no gaussianos (no normales). Su diferencia fundamental con los métodos estadísticos multivariantes clásicos radica en el supuesto de no gaussianidad, lo que permite la identificación de componentes originales subyacentes, en contraste con los métodos clásicos.
## ¿Qué es Beamforming?
Esta es una técnica que permite mejorar la captación de señal en una dirección específica y reducir el ruido o interferencias que puedan provenir de otras direcciones, esto es posible si se utiliza un arreglo de sensores siendo micrófonos o antenas que reciben la misma señal con algunas diferencias de tiempo, después estas señales se ajustan aplicando retrasos y pesos (retrasos y pesos) antes de ser sumados lo que refuerza la señal deseada atenuando las de más. Existen varios métodos para la implementación de beamforming, podríamos hablar de lo convencional el cual usa retrasos (Delays) fijos para cada sensor, en el adaptativo que ajusta dinámicamente los parámetros mediante algoritmos de adaptación siendo esta técnica utilizada en las comunicaciones inalámbricas, procesamiento de voz y en biomédica hablaríamos de la detección del latido fetal.
## Diferencia entre ICA y BEAMFORMING
Podemos decir que ICA intenta separar múltiples señales que han sido mezcladas mientras que beamforming se enfoca en mejorar la señal desde una dirección específica. La siguiente tabla explica mucho mejor lo anterior mencionado.



 ![{9636A8FF-1E1A-44F0-98B7-2692BC0D1C35}](https://github.com/user-attachments/assets/74c10c3d-5310-40d1-80ec-72967d3cf53d)

 ### Procedimiento y resultados 
Primero se subio cada uno de los audios en formato wav 
 ```
files = ["pa.wav", "sa.wav", "cri.wav"]
signals = []
sr = None
```
Luego se calculo el SNR de cada voz con la siguiente funcion
 ```
def calculate_snr(signal, noise):
    signal_power = np.mean(signal ** 2)
    noise_power = np.mean(noise ** 2)
    return 10 * np.log10(signal_power / noise_power)
```
![image](https://github.com/user-attachments/assets/9a2e5ad3-7e2c-48f0-af70-bf451b150e02)

Se aislo la voz mas predominante con ICA y se obtuvo la siguiente grafica

![voz_aislada](https://github.com/user-attachments/assets/1dc1f29b-dc61-4348-b10a-f1753f2b130b)
*Voz aislada*

utilizando la siguiente funcion
 ```
# Aplicar FastICA para separar la voz
ica = FastICA(n_components=3, max_iter=500)
sources = ica.fit_transform(signals.T).T
correlations = [np.max(np.abs(correlate(s, signals[0], mode='valid'))) for s in sources]
voz_cri = sources[np.argmax(correlations)]
```

Para realizar el analisis temporal y espectral de las señales se realizo la transformada de fourier y la densidad espectral, obtuvimos lo siguiente
![image](https://github.com/user-attachments/assets/be246c67-c8c8-4613-a00a-69a10d125666)







### ¿Cómo afecta la posición relativa de los micrófonos y las fuentes sonoras en la efectividad de la separación de señales?
La posición de los micrófonos y las personas es importante para poder separar las voces en el audio, ya que si los micrófonos están muy juntos o en línea con las personas, la señal se mezcla y es mucho más difícil separarlo.
### ¿Qué mejoras implementa en la metodología para obtener mejoras en el resultado?
Para mejorar la separación de las voces se podría hacer lo siguiente, colocar los micrófonos en mejores posiciones para captar mejor el sonido y utilizar mejores dispositivos para capturar el sonido.

## Recomendaciones
-Python 3.9, pyedflib, matplotlib

## Información de contacto
-est.paula.vcardenas@unimilitar.edu.co, est.sara.martin@unimilitar.edu.co, est.cristian.cmolina@unimilitar.edu.co

## Referencias 
https://pmc.ncbi.nlm.nih.gov/articles/PMC3538438/
https://www.nti-audio.com/es/servicio/conocimientos/transformacion-rapida-de-fourier-fft
Plaza, DHO (2018). Construcción de un arreglo de altavoces y su aplicación en audio personalizado (beamforming) (Tesis doctoral, Universidad de San Buenaventura Colombia).


