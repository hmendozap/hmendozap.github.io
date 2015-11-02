---
layout: post
title: Pobre o no pobre<br \>Esa es la cuestión (de cantidad)
---
Hace algunas semanas se dieron a conocer los resultados de la encuesta 2014 del [Instituto Nacional de Instituto de Desarrollo](http://www.inide.gob.ni/) (INIDE) y uno de las observaciones que más llamaron la atención fue la reducción _drástica_ de la pobreza a nivel nacional. Ver [artículo](http://confidencial.com.ni/pobreza-bajo-de-42-5-a-29-6/).

Estos resultados a primera vista son bienvenidos pero como dicen por ahí en mi pueblo "Como puede ser que sí, puede ser que no" y el detalle no radica principalmente en la encuesta sobre el bienestar en sí, si no en como se mide, o se ha medido hasta ahora, la pobreza en el mundo.  Existen académicos que han criticado e incluso han propuesto nuevas medidas para calcular los umbrales o líneas de pobreza ([Detalles al estimar la pobreza. En inglés](http://ineteconomics.org/ideas-papers/blog/is-the-devil-in-the-details-estimating-global-poverty)). También "The Economist" en uno de sus artículos en línea duda, no de la autenticidad de estos datos sino de la realidad que presentan y lo llaman el [truculento esfuerzo de medir la pobreza.](http://www.economist.com/news/finance-economics/21673530-number-poor-people-declining-data-are-fuzzy-tricky-work-measuring-falling)

Como buen ingeniero y con algo de tiempo libre, decidí de tratar de reflejar la difícil tarea que es medir la pobreza. Todas las gráficas mostradas en el artículo fueron creadas por su servilleta, a menos que se indique lo contrario.

*Nota aclaratoria: Debido a que la información es recopilada de diversas fuentes es sensato tomar los valores como aproximados y con algo de escepticismo.*

* Primero está la ardua tarea de recopilar la información. Dado que la reducción de pobreza ha sido parte de las políticas públicas de varios organismos internacionales, en teoría existen varias bases de datos de donde obtener información. Pero en palabras del gran Cantiflas: **"ahí está el detalle"**. La información está dispersa entre organismos, los datos no son los mismos, incluyen diversos pies de página y notas y aclaraciones y es bastante laborioso poder comparar la información. Incluso el Banco Mundial advierte de esta [tarea](http://www.bancomundial.org/es/news/press-release/2015/10/15/world-bank-new-end-poverty-tool-surveys-in-poorest-countries).

* Para esta recopilación se tomaron como fuentes:
    + [CEPALSTAT](http://estadisticas.cepal.org/cepalstat/web_cepalstat/openDataAPI.asp?idioma=e): Bases de datos y de publicaciones estadísticas de la Comisión Económica para América Latina y el Caribe (CEPAL)
    + Encuesta del INIDE. [Presentada el 06 de octubre de 2015](http://www.inide.gob.ni/Emnv/Emnv14/RESULTADOS%20DE%20POBREZA%202014%20I%20INIDE.pdf)
    + [PovCalNet](http://iresearch.worldbank.org/PovcalNet/index.htm?0,3): Base de datos interactiva del Banco Mundial para la medición de pobreza
    + [BID - Latin Macro Watch](http://www11.iadb.org/es/investigacion-y-datos/latin-macro-watch/latin-macro-watch-tablas-de-paises,18579.html): Base de datos macroeconómicos y financieros recopilados por el Banco Interamericano de Desarrollo (BID)

Después de "limpiar" y "depurar" (aka. data munching) obtenemos los siguiente población en pobreza para Nicaragua a través de los años:

![Pobreza en Nicaragua según diversas instituciones](/img/poverty/poverty-nic-institution.png "Pobreza por instituciones ")

Los puntos en la gráfica anterior son proporcionales al porcentaje de gente pobre en el país, entre más grande el punto más gente vive en pobreza.

Queda en obviedad la marcada varianza que existe al medir la pobreza, para CEPAL una de las mediciones de lo que significa ser pobre es vivir con menos de $4 dólares al día, pobreza para el Banco Mundial a través de CEPALSTAT es subsistir con menos de $1.90/día al 2011 y varía en cuanto si las cifras están basadas en ingreso y consumo (una gran diferencia véase [Table 2](http://ineteconomics.org/ideas-papers/blog/is-the-devil-in-the-details-estimating-global-poverty)); la información de PovCalNet es creada con una línea de $1.90 al 2011 a Paridad de Poder Adquisitivo ([PPA](https://es.wikipedia.org/wiki/Paridad_de_poder_adquisitivo)); INIDE no ofrece datos (al menos no encontré, existe un acta del evento de presentación pero no se mencionan cifras) acerca de cual línea fue usada pero se puede calcular basado en los datos del 2009, que es uno de los pocos años en los cuales existe información consistente.

Cada punto es la población que vive en pobreza en Nicaragua si se toman diferentes líneas base, por lo tanto si calculamos la pobreza con consumo mínimo de $1.10 la proporción es menor a 5% y así sucesivamente:

![Pobreza con diferentes lineas bases](/img/poverty/poverty-level-nic-2009.png "Pobreza dependiendo del consumo mínimo")

INIDE tiene figuras de 14.6 % de población en pobreza en para el año 2009, que *sugiere* una línea de pobreza de ca. $2.15 y un 8.3% para el 2014. Ahora, estos datos generan dos posibilidades:

* **Menos pobres, pero pobres más extremos**
La línea de pobreza entre mediciones a través de los años es la misma (es decir no ajustada a la inflación), entonces hubo disminución en cuanto al porcentaje de gente pobre, pero estas personas son muchísimo más pobres que lo eran hace cinco años es decir un dólar ($1) en 2009 compraba más que un dólar en 2014.

* **Nicaragua a la par de Perú, Paraguay, Ecuador**
Obviamente según la métrica de pobreza y de ingreso (primero es PIB, luego es ingreso promedio) pero el argumento es el siguiente: La línea de pobreza en la encuesta sí fue ajustada a la inflación, ahora es $2.9 y teniendo solamente un 8% de la población como pobre, no está muy lejano de la situación (la nueva situación de Nicaragua sería entonces el punto azul) en Ecuador (8.92%), Perú (6.27%), Paraguay(6.4%) e incluso El Salvador(6.4%), según datos del PovCalNet del Banco Mundial. (Véase figuras siguientes.)

![Pobreza vs. PIB en América Latina](/img/poverty/poverty-pib-latam-2009.png "Oh si Nicaragua fuera más rico")
![Pobreza vs. Ingreso medio en América Latina](/img/poverty/poverty-mincome-latam-2009.png "Hay que calcular el cluster")

La suposición de una línea de $2.15 para el 2009 puede bien ser errónea, pero esto supone que si es menor (alredor de $1.90) el país en 2009 realmente era más pobre que las cifras sugieren o si la línea inicial es mayor los dos escenarios previos son muchísimo más extremos: **los pobres más pobres o Nicaragua muchísimo más rico**.

Nada de lo anteriormente expuesto es definitivo, ya que a pesar de tener algunos datos sobre la pobreza, ingreso y consumo en Nicaragua, la mayoría están incompletos. No es como el servicio nacional de El Salvador que no ha presentado cifras al CEPALSTAT en los últimos años pero sería preferible para la transparencia dentro del gobierno que la mayoría de los datos sean libres para ser analizados por políticos, estadistas, académicos y la población en general.

Esto ha sido mi intento por darle alguna claridad a los datos de pobreza en específico en Nicaragua, claro que todavía queda mucho por hacer y se hará eventualmente. Por lo pronto mi siguiente idea para visualizar es acerca del béisbol en Nicaragua, si alguien me puede echar la mano con conseguir la info, echéme un tweet o si tienen alguna idea y quieren trabajarla en conjunto, también aplica.

--- 
Breve actualización: Recomiendo leer esta pieza, que aunque no tan pulida refleja la [situación con rostros](http://www.laprensa.com.ni/2015/11/01/boletin/1928752-rostros-de-la-pobreza-2) sobre las nuevas medidas de pobreza.