---
layout: post
title: Baseball Nica <br /> Visualización (Parte I)
hide: true
---

Después del [desahogo]({% post_url 2015-11-03-pepenando-datos %}) ahora sí, a conocer un poco más del beisbol amateur de Nicaragua alias _"Pomares"_.

Se recopilaron datos de la Pomares en vez de la liga profesional, porque pues en la Pomares hay más datos. La mayoría de los datos entre 2009-2012 son de toda la temporada, incluyendo playoffs aparenteme, y son datos bastantes básicos. No son los datos de la base Lahman, Sabermetrics o Pitchf/x que registran incluso el tipo de lanzamiento y la zona que llegó al home, pero creo que se puede generar algo con esto.

Como sudé para la limpieza de datos (Data Munging) usaré este dataset para al menos otros dos posts: **visualización y estimación**, **cambios históricos y tendencias** y **predicciones**.

### Consistencia - Estimación Bayesiana

Aquí trataremos de contestar la pregunta: ¿Quién ha tenido el mejor promedio de bateo en esos cuatro años? Al ver los datos, hay un par de nombres que todavía se me hacen conocidos: Marlón Abea, Sandor Guido, Norman Cardoze! Pero entonces eso quiere decir que siguen en el deporte con 45+ años. Wow, pero claro todo esto es conjetura ya que no tengo los datos de las fechas de nacimiento. Siguiendo.

Para responder la pregunta nos basaremos en un método bastante sencillo: Estimación bayesiana, que nos permite hacer una comparación válida para bateadores experimentados que tienen, qué se yo, 50 hits en 200 veces al bat y el novato que tiene 30 en 100. Para seguir con el método recomiendo bastante el [post](http://varianceexplained.org/r/empirical_bayes_baseball/) que usé como referencia.

Empezamos visualizando la distribución del promedio para bateadores que no son lanzadores (_pitchers_) y que tienen más de  20 intentos en el plato. Obviamente es mejor tomar bateadores que tengan más intentos, ya que los que tienen muy pocos introducen error y sesgo a la hora de _"ajustar"_ distribución. Pero, pues, a falta de datos nos quedamos con más de 20 que para nuestro caso es suficiente.

![Distrubicion bateo Pomares](/img/beis/ave_distro.png )

En la gráfica se puede apreciar que hemos _"ajustado"_ una distribución a nuestros promedios. La media de todos los bateadores es cerca de $$0.253$$, un poco más bajo que las grandes ligas, pero en general bien. La distribución que se usó se llama [distribución](http://en.wikipedia.org/wiki/beta_distribution) distribución $$\beta$$ que intituivamente se puede pensar como una posible distribución de probabilidades (El promedio de bateo por definición es una probabilidad) tiene dos parámetros con valores $$\alpha_0 = $$ y $$\beta_0 = $$ para el ajuste.

Luego se recalcula la estimación de los nuevos promedios (**"AVE_E"** en la tabla) y se ordenan y obtenemos lo siguiente:

|-----------------|-----|---|---------|---------|
| PLAYER          | H   | AB|    AVE  |   AVE_E |
|-----------------|-----|---|---------|---------|
|Jimmy_Gonzalez   | 240 |577| 0.415945| 0.405290|
|Juan_Oviedo      | 326 |907| 0.359427| 0.354667|
|Justo_Rivas      | 301 |842| 0.357482| 0.352450|
|Jilton_Calderon  | 276 |772| 0.357513| 0.352044|
|Ofilio_Castro    | 211 |588| 0.358844| 0.351685|
|Juan_Blandon     | 255 |734| 0.347411| 0.342147|
|Dwight_Britton   | 208 |602| 0.345515| 0.339268|
|Ernesto_Garay    | 304 |894| 0.340045| 0.335972|
|Antenor_Lopez    | 202 |593| 0.340641| 0.334585|
|Juan_Ramon_Flores|  28 | 73| 0.383562| 0.33444 |
|-----------------|-----|---|---------|---------|

Tabla de los bateadores más consistentes.

¿Qué tal? Jimmy González es el bateador que mejor promedio tuvo en esos cuatro años. Ja! Todavía recuerdo que jugaba cuando terminé secundaria y aparentemente ha seguido con buen paso a nivel nacional. En al siguiente gráfica se puede ver lo "anómalo" o por decirlo de una manera más a tono con el deporte, lo "dominante" que es su promedio en comparación a los otros _Top-9_:

![Top 10 promedios de bateo](/img/beis/top_10_batters.png )

