---
layout: post
title: Pepenando datos porque pues soy de un país tercermundista
hide: false
---
La verdad esta entrada la iba a escribir con muchísimo más odio y rencor pero estoy un poco más calmado después de haber empezado con el análisis y la visualización y lograr producir [algo decente]({% post_url 2015-11-04-beis-nica-parte1 %}). Habiendo dicho eso:

> ¡¿Qué putas, Nicaragua!? o mejor dicho ¡¿QUÉ HIJUELAGRANPUTAS BEISBOL DE NICARAGUA?!

Todo surgió por un comentario que alguien hizo en twitter sobre Chocolatito siendo mejor que Alexis de lo cual aún no estoy convencido, pero eso será para otro momento y pensé: "estaría cool poder hacer análisis de datos para deportes en Nicaragua y no solo boxeo".

Decidí empezar con beisbol por las razones obvias, el deporte ha estado relacionado con números, estadísticas desde la formación de las Grandes Ligas (MLB) a finales del siglo 19 (por ahí de 1884 si no mal recuerdo) incluso hay una película la cual una gran parte de la trama está centrada en análisis estadístico para ayudar al rendimiento de un equipo. Sí, sí es [Moneyball](http://en.wikipedia.org/wiki/Moneyball_(film)), si no la han visto háganse un favor y véanla, además [Andy Dwyer-Ludgate!](https://en.wikipedia.org/wiki/Chris_Pratt) y el dos veces nominado al oscar, [Jonah Hill](https://en.wikipedia.org/wiki/Jonah_Hill).

Decidido inicié la búsqueda por internet y revisé los lugares obvios:

* La recién re-iniciada **Liga Nicaragüense Beisbol Profesional** [(LNBP)](http://lbpn.com.ni/)

* La _nueva_ página de la **Liga Amateur de Nicaragua** [ (Pomares)](http://www.beisbolgpo.tk/#)

* También en la Federación Nicaragüense de Beisbol Amateur [ (Feniba)](http://www.feniba.org/)

Pero no estaba preparado para lo encontré, las pocas estadísticas que existen están dispersas por todos lados de cada sitio, no hay ninguna estructura _whatsoever_ sobre la organización de la información, puedo más o menos entender la dificultad de la digitalización de datos antes del 2009, pero llenar un pdf con imágenes escaneadas eso es simplemente ser haragán. Si son como, dice mi abuelita, "Santo Tomás" vayan, vayan y visiten los sitios en la lista anterior, luego me dan sus opiniones.

Por un momento decidí cancelar el post y cualquier análisis subsecuente, pero no voy a dejar que un simple "no se puede" me detenga tan fácilmente. Pues nada me di la tarea de convertir los datos de bateo y pitcheo (¿picheo?) para la Pomares del 2009 al 2012. Quería hacerlo hasta 2014, porque en el 2015 el formato de los documentos cambió, incluyeron más datos y es más fácil el parseo, pero adivina adivinador, **no existen** los datos de la Pomares 2013-2014!!!

Entonces :

+ Encontrar una herramienta de reconocimiento de caracteres (OCR) gratuita y con una certeza de reconocimiento lo suficientemente alta. Existen muchas en el mercado pero la mayoría cuesta dinero y uno que es [pobre]({% post_url 2015-10-22-pobre-o-no-pobre %}), tiene que ajustarse.

+ Al no tener experiencia con OCR (python-tesseract) caí en errores de novato. Pasé todo un sábado tratando de hacerlo compilar, entrenar y crear mi base de reconocimiento, pero eso simplemente no tiene sentido. Como decía mi profesor de biología en la secundaria: "Cada vez que haces un experimento, no empiezas descubriendo el fuego"

+ Tuve suerte y encontré [gImageReader](http://sourceforge.net/projects/gimagereader/) y mi salvadora [onlineocr.net](http://www.onlineocr.net/) que a través de su servicio gratis de 15 páginas gratis por hora (del cual abusé!) pude terminar la transcisión relativamente rápido. MUCHAS GRACIAS POR EXISTIR onlineocr.net!

+ Las imágenes fueron producidas al ser impresas con una impresora de matriz de puntos y para [mejorar](http://usabilityetc.com/2009/01/improve-dot-matrix-ocr-performance-tutorial/) la precisión del OCR, engrandé y limpié las imágenes con [imagemagick](http://www.fmwconcepts.com/imagemagick/textcleaner/) para luego pasarlas al servicio de OCR.

+ Revisé, consolidé y guarde los datos usando MS Excel, más que todo por que ya tenía experiencia usando VBA y macros, que facilitaron enormemente la tarea.

Al final pasé de esto:
![Datos Originales de Pomares](/img/beis/screen_01.png "Eran scans ¬¬")

a esto:

![Datos Finales Pomares](/img/beis/screen_02.png "Algo trabajable :)")

Me tardé 10 días trabajando medio día más o menos, algunos días más, algunos días menos. Si una persona puede hacerlo en una semana y media trabajando medio tiempo, solo se necesitan 2 ó 3 personas máximas durante dos horas, para pasar los datos a manera digital, no estoy pidiendo que hagan una base de datos como la [Lahman](http://www.seanlahman.com/baseball-archive/statistics/), o el [Armchair Analysis](http://armchairanalysis.com/) de la NFL, pero algo que se pueda parsear de manera programática y no depender de herramientas para reconocimiento de caracteres.

Todo este escrito tiene una enseñanza: **Todas estas cosas de malos datos y mala disponibilidad de datos se pueden mejorar en Nicaragua**. Es cierto, somos un país tercermundista y pobre hasta eso, pero eso no quiere decir que tengamos que ser así siempre. Puedo escuchar perfectamente el argumento: "¿De que le sirve a Nicaragua datos frívolos de beisbol? Lo que la gente necesita es comida, educación y salud".

Cierto, pero este tipo de pensamiento cae en una falacia: "Urgente le quita lugar a lo importante". Además análisis y visualización de datos es una herramienta importante para políticas públicas y [desarrollo sustentable](http://blogs.iadb.org/ciudadessostenibles/2015/11/03/urban-dashboard/). ¿Cómo vamos a transmitir la inormación de [gastos de nuestro gobierno](https://twitter.com/laprensa/status/661606399907090432) si no somos todos hábiles a la hora de leer números y datos? Con una infografía, visualización o incluso una tabla!

Último punto, hace poco empezó el [#DALNIC2015](https://twitter.com/hashtag/DALNIC2015?src=hash) con el apoyo del Instituto de Estudios Estratégicos y Políticas Públicas [(IEEPP)](https://twitter.com/ieepp) para la creación de herramientos (apps/data) para el uso de la sociedad civil y saben qué es algo que necesita Nicaragua? Una herramienta liviana, accesible, que se pueda usar en el campo y en la ciudad para la digitalización de datos. Existen pruebas de concepto con Raspberry Pi, smartphones (que no necesariamente son de última generación) y computadoras sin mucha capacidad de procesamiento.

Téngalo emprendedores de Nicaragua, _low-hanging fruit_.
