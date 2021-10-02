---
layout: post
title:  "August 2021 AWS Deepracer Open Division"
author: ana
categories: [ Reinforcement learning ]
image: assets/images/2021-09-02-aws-deepracer.png
---

Una adictiva forma de aprender *reinforcement learning*.

Dentro de las actividades recomendadas para el curso de Udacity [**AWS Machine Learning Foundations**](https://www.udacity.com/course/aws-machine-learning-foundations--ud065) conocí el programa [AWS DeepRacer](https://aws.amazon.com/es/deepracer/). Nada mejor que la gamificación bien aplicada para enganchar al aprendizaje. DeepRacer es completamente adictivo. Se trata de un programa en el que tenemos que porgramar la función de recompensa, en python, de un coche autónomo para que aprenda a circular solo por los circuitos disponibles. Hay varios tipos de competición en las que el objetivo puede variar:
- Time-trial: recorrer un circuito a la mayor velocidad posible sin salirse de pista,
- Object avoidance: como el anterior pero con el añadido de objetos inmóviles a esquivar y 
- Head-to-head racing: competir contra otros vehículos en la misma pista y que llegar el primero a línea de meta.

El pasado verano aproveché para echarme unas partidas con la capa gratuita de AWS que incluye 10 horas para entrenar y evaluar los modelos durante el primer mes desde la creación de una cuenta. Tened cuidado porque AWS no os avisará si superáis ese límite. El coste aproximado de una hora de SpeedRacer es de $3,5, actualmente. En este enlace tenéis la información actualizada de [precios de uso de AWS DeepRacer](https://aws.amazon.com/es/deepracer/pricing/).

En DeepRacer existen 3 categorías o ligas de competición:
- **Open Division**: es la división o liga de acceso. Cada mes el 10% de los competidores con el mejor tiempo pasan a la liga intermedia o:
- **Pro Division**: los ganadores de esta división pueden conseguir premios como [coches DeepRacer Evo](https://www.amazon.com/dp/B081GZSJVL), y finalmente acceder a: 
- **Pro Division Finale**: al final de cada mes los 16 mejores corredores de la Pro Division compiten uno contra otro en una carrera que transmite en directo. El ganador es recompensado con un programa educativo de Machine Learning valorado en $20.000.

En la competición del pasado mes de agosto (2021) quedé en la posición 125 de 1636 participantes. Lo que me clasificó para la Pro Division.

![Clasifición Open Division Agosto 2021 - Casiopa](/assets/images/2021-09-02-aws-deepracer-clasificacion-agosto.png)


<iframe width="560" height="315" src="https://www.youtube.com/embed/6Y97u64mE8E" title="AWS AugustQualifier Casiopa" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<p></p>

Enlaces interesantes para inciarse en AWS DeepRacer:
- Vídeo: [What is AWS DeepRacer?](https://www.youtube.com/watch?v=vCt-F2HscOU)
- Vídeo: [Get hands on with AWS DeepRacer](https://www.youtube.com/watch?v=43zqI0n4D7A)
- Repositorio GitHub: [AWS DeepRacer Workshops](https://github.com/aws-samples/aws-deepracer-workshops)
