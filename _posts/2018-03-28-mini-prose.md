---
layout: post
title: Sintetisando mini texto con ProSE SDK
tags: [prose, program synthesis, experiences]
---

Este es un mini-post acerca de mis experiencias con
[ProSE SDK (Program Synthesis using Examples SDK) de MSFT.](https://microsoft.github.io/prose/)

Últimamente hemos realizado bastantes actualizaciones en [MCITCSA](http://www.mcitcsa.net).
El detalle es que muchas de estas son actualizaciones a _"medias"_ porque debido
a la carga de trabajo no hemos terminado la migración completa y como buen
ingeniero uno quiere aliviar esta carga. Digo por eso existe la tecnología
en el mundo para disminuir el trabajo que nos toca realizar pero obteniendo los
mismos beneficios.

Dentro de esas ideas, encontré ProSE SDK. Así fue que conocí sobre **Program Synthesis**
 o síntesis de programas. La idea es sencilla:

Se toman el par de ejemplo que produce un resultado $$\lt e, r \gt$$,
de manera tal que se pueda generar una transformación o una traducción que mapea el ejemplo
con el resultado ($$e \rightarrow r$$). De esta transformación de ejemplo a resultado
se sintetiza un programa $$\mathcal{P}$$ y listo! Ahora cada vez que se 
ejecute $$\mathcal{P}$$ con otros parámetros, este debería producir un 
resultado similar a los de los ejemplos.

Si les quedó un poco de duda, veamos la demostración hacen los muchachos de PROSE
para transformación de texto:

 - HARMONND, JOEL $$ \rightarrow $$ J. Harmonnd.

Aquí tenemos nuestro par ejemplo (HARMONND, JOEL) y resultado (J. Harmonnd),
después de hacer la síntesis, obtenemos un programa nuevo $$\mathcal{P}$$. Que cuando llamemos
con nuevos ejemplos producirán nuevos resultados:

- ROMMEL, TOMAS $$ \rightarrow $$ T. Rommel. 
- SALAS, ALEXIS $$ \rightarrow $$ A. Salas.

Si han trabajo con [Excel](https://en.wikipedia.org/wiki/Microsoft_Excel) 
y su opción [_flash fill_](https://www.microsoft.com/en-us/research/publication/automating-string-processing-spreadsheets-using-input-output-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashfill.html)
estos ejemplos se les harán conocidos. De hecho la investigación de _flash fill_ de Excel es la misma
que ProSE.

Este caso de uso es uno de tantos que existen para ProSE, otros incluyen extracción
de datos en texto estructurado (Web y JSON), transformación de texto
y generación de programas para usos específicos.

## Del juego a la realidad

_Back to the main point_, después de jugar y leer un poco más acerca de ProSE,
decidí aplicarlo a la refactorización que estamos realizando. Primero intenté
con una sección de código pequeña y utilizando transformación de texto tal cual,
sin tener que programar el árbol de sintaxis abstracta o la gramática 
específica a nuestra refactorización.

Es decir obligar que el _framework_ utilice el texto a transformar como texto plano
, sin estructura especifíca definida.
(Para más detalle leer: [PROSE A Tutorial](https://microsoft.github.io/prose/documentation/prose/tutorial/))

Lo que necesitaba recodificar era lo siguiente: 

{% highlight c# %}  
if (Request.QueryString["type"] != null && Request.QueryString["type"] != "")
    hfType.Value = Request.QueryString["type"];
else
    hfType.Value = "";
{% endhighlight  %}  

A algo un poquito más legible:

{% highlight c# %}  
hfType.Value = Request.QueryString["type"];
if (String.IsNullOrEmpty(hfType.Value)) {
    hfType.Value = "";
}
{% endhighlight  %}

La primera transformación la hice manual, pero no iba a recodificar 4 campos más
a mano. (El porqué existen tantos campos así , es la razón por la cual se está
haciendo refactorización). Es el momento para brillar de ProSE.
Después de modificar levemente el código de ejemplo para incluir mi par ejemplo,
resultado, generé el programa sintetizado y lo corrí con los 4 campos más para
obtener una nueva refactorización. 

Aquí el resultado:

{% highlight c# %}  
hfObjectiveId.Value = Request.QueryString["oeid"];
if (String.IsNullOrEmpty(hfObjectiveId.Value)) {
    hfObjectiveId.Value = "";
}

hfResultId.Value = Request.QueryString["rid"];
if (String.IsNullOrEmpty(hfResultId.Value)) {
    hfResultId.Value = "";
}

hfProjectId.Value = Request.QueryString["pid"];
if (String.IsNullOrEmpty(hfProjectId.Value)) {
    hfProjectId.Value = "";
}

hfPlanId.Value = Request.QueryString["planid"];
if (String.IsNullOrEmpty(hfPlanId.Value)) {
    hfPlanId.Value = "";
}
{% endhighlight  %}

Lo mejor de todo es que no tuve que codificar ninguna propiedad explícita acerca
de lo que estaba haciendo, solamente puse mis ejemplos y _voilà_.

## Volando muy cerca del sol

Es momento ahora de hacer cosas más ambiciosas, en vez de refactorizar unas
cuantas funciones, vamos a refactorizar todo un archivo. Para iniciar creé mis
dos archivos, el de muestra o ejemplo y el refactorizado.

¿El resultado? Pues no pude saber, ProSE generaba un `IOException: Memory Error`,
imagino que al tomar todo el archivo como texto, ProSE trata de generar un programa
que tome todo el archivo sin contexto y sin división alguna, algo así como tener
todo el texto en una celda de excel y tratar de hacer un _flash fill_ en la
siguiente celda. Lo que imagino es demasiada carga para hacer una transformación
de una sola vez, algo así como comerse una ballena de un solo bocado: no se puede.

## Lecciones aprendidas

ProSE es una herramienta que puede ser muy útil, especialmente en la interacción
con el usuario final: autocompletar, transformación de nombres en texto
generación de nombres para elementos. Realizar las pequeñas transformaciones de
código tienen su aplicación aunque sea a pequeña escala.

Dentro de los siguientes pasos sería realizar una transformación utilizando
propiamente una grámatica para nuestra aplicación o hacer la transformación de
manera escalada en pequeños pedazos.

## Si te interesa

Si les llama la atención lo que es ProSE y quieren conocer más sobre esta tecnología,
les recomiendo visitar los siguientes vínculos:

- [Prose Samples](https://github.com/Microsoft/prose)
- [Prose Tutorial](https://github.com/gustavoasoares/prose-tutorial/wiki/Prose-tutorial)
- [Refazer](https://github.com/gustavoasoares/refazer)


------------------------------------------------
Nota: La abreviación ProSE es formateo propio, slo porque pienso que se ve mejor así.