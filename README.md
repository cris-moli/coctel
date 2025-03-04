# Coctel
 ## Introducción
En este trabajo desarrollaremos la práctica de “la fiesta de cóctel”, esta consiste en grabar diferentes conversaciones desde diferentes micrófonos en una reunión, en nuestro caso hicimos uso de la aplicación grabadora de voz desde los celulares, en un cuarto insonoro a una distancia de aproximadamente 2 metros cada uno de los micrófonos que se encontraban en un punto central, esto permitió la captura de tres audios guardados desde tres diferentes celulares de aproximadamente 15 segundos cada audio. 

## ¿Qué es ICA?
El análisis de componentes independientes es un método probabilístico para aprender una transformación lineal de un vector aleatorio. El objetivo es encontrar componentes que sean máximamente independientes y no gaussianos (no normales). Su diferencia fundamental con los métodos estadísticos multivariantes clásicos radica en el supuesto de no gaussianidad, lo que permite la identificación de componentes originales subyacentes, en contraste con los métodos clásicos.
## ¿Qué es Beamforming?
Esta es una técnica que permite mejorar la captación de señal en una dirección específica y reducir el ruido o interferencias que puedan provenir de otras direcciones, esto es posible si se utiliza un arreglo de sensores siendo micrófonos o antenas que reciben la misma señal con algunas diferencias de tiempo, después estas señales se ajustan aplicando retrasos y pesos (retrasos y pesos) antes de ser sumados lo que refuerza la señal deseada atenuando las de más. Existen varios métodos para la implementación de beamforming, podríamos hablar de lo convencional el cual usa retrasos (Delays) fijos para cada sensor, en el adaptativo que ajusta dinámicamente los parámetros mediante algoritmos de adaptación siendo esta técnica utilizada en las comunicaciones inalámbricas, procesamiento de voz y en biomédica hablaríamos de la detección del latido fetal.
## Diferencia entre ICA y BEAMFORMING
Podemos decir que ICA intenta separar múltiples señales que han sido mezcladas mientras que beamforming se enfoca en mejorar la señal desde una dirección específica. La siguiente tabla explica mucho mejor lo anterior mencionado.



 ![{9636A8FF-1E1A-44F0-98B7-2692BC0D1C35}](https://github.com/user-attachments/assets/74c10c3d-5310-40d1-80ec-72967d3cf53d)

## Recomendaciones
-Python 3.9, pyedflib, matplotlib

## Información de contacto
-est.paula.vcardenas@unimilitar.edu.co, est.sara.martin@unimilitar.edu.co, est.cristian.cmolina@unimilitar.edu.co

## Referencias 
https://pmc.ncbi.nlm.nih.gov/articles/PMC3538438/


