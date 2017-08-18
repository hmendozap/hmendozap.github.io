---
layout: post
title: Nuevos horizontes como jefe de desarrollo en MCITCSA
---

Estar de regreso en Nicaragua, es un buen sentimiento desde la parte personal, de estar de regreso en el país donde crecí. Pero desde el aspecto laboral y de investigación deja un poco (mucho) que desear. Después de haberlo pensando y repensado decidí quedarme aquí y trabajar para la empresa que mi padre fundó: **MCITCSA**.

## Pero es consultoría y no investigación

**MCITCSA** (pronunciado _emecitsa_) se dedica en parte al desarrollo web desde diseño de datos, código de servidor y manejo de bases de daos. La otra parte se dedica a realizar consultorías basadas en gerencia de proyectos _(Project Management)_. Honestamente es algo que nunca me imaginé haciendo de joven, después de la tesis la investigación y los sistemas embebidos es lo que más me interesa.

Así como dice la frase: _"No existen cosas aburridas. Solo gente aburrida. Todo es interesante en esta vida."_ Entonces decidí tomar esto como un reto más y aplicar lo que he aprendido
 utilizándolo para mejorar la empresa y en muy pequeña medida la sociedad.

Lo bueno (o malo, dependiendo de cómo se vea) es que el puesto de jefe de desarrollo es un buen lugar para empezar a formar una fuerte y (espero) exitosa área de innovación y de investigación. Sí, así como lo leen, aquí en MCITCSA mi meta es hacer investigación.

## Bastante tareas: Update, research and implement

Con el ideal de hacer investigación, también va de la mano la aplicación de nuevas ideas. Cuando la empresa se fundó, allá por el muy pasado 2009 (casi 20 años), se desarrolló usando el famoso _ASP.NET_, que a pesar de todas sus limitaciones, son soluciones que todavía están en producción, especialmente en sistemas _legacy_. Imagino que la decisión de utilizar herramientas "Microsoft" fue por necesidad de compatibilidad de plataforma con la mayoría de los clientes y también por el famoso VB 6 ( Mi padre cuenta la anécdota que mucha gente estaba en contra y quedaron usando FoxPro!!)

### .NET Core

Pero el 2009 ya está en el pasado, y ahora lo _inn_ es .NET Core, un _framework_ multiplataforma, desarrollado recientemente por _Microsoft_, pero que está ganando popularidad por su habilidad de correr en Linux, Windows y macOS con el mismo código y además es Open Source.

Otra ventaja de tener .NET Core, es la migración al ya conocido MVC _(Model-View-Controller)_ una arquitectura de diseño para el desarrollo de web, ya sea desktop y móviles. Inicialmente estaba un poco renuente para usarlo, principalmente porque no lo conocía, pero ya una vez empezamo a desarrollar en el, veo que se convertirá en una pieza importante para las nuevas interfaces y aplicaciones de MCITCSA.

### Azure Web :space_invader:

Siguiendo la migración a la _nueva interwebs_, hemos optado por mover algunos productos a la plataforma de _cloud computing_ de Microsoft: **Azure.** (No se me ocurre otra traducción para cloud computing sino computación en la nube :cold_sweat:, entonces mejor así nos quedamos)

Habiendo trabajado en Amazon Web Services (AWS) y la experiencia de tener cobros a demanda y pagar solo por lo que se utiliza, creo conveniente el de tener cierto orden en como se desarrollan nuestros servicios y así poder ser más eficientes y productivos al momento de desplegar y entrar _online_.

### Data, Data and Data

> Es el petróleo del futuro.

Así como lo dice _The Economist_, la información generada por los usuarios se ha convertido de alguna manera en una mina de oro, pero a diferencia del oro: no es exactamente brillante, tiene que pasar por tubería pero digital, y tiene que ser pulida y transformada. Aquí en MCITCSA esperamos utilizar esa materia prima y poder transformala en algo de valor para el usuario final, siempre con la meta de poder ayudar y dar mejor servicio.

### F#

Mientras terminaba la maestría, me di a la tarea de aprender algo nuevo, fuera de mi zona de comfort, y decidí aprender un lenguaje de programación funcional, en este caso fue **Haskell**, pero quedé encantado, programación funcional es más elegante y a mí humilde opinión, es algo que todo desarrollador necesita aprender, porque se convierte en una herramienta más para realizar tareas de manera más eficiente. Especialmente después de haber mencionado la necesidad de trabajar con datos y más datos.

Siguiendo el uso de .NET en la empresa, decidimos entrar a fase de prueba en varios casos de uso con **F#**, la versión de programación funcional de Microsoft, pero que actualmente es desarrollado de manera open source. Esperamos que el uso de **F#** se convierta en algo estándar para el uso de herramientas dentro de la empresa. Estoy convecido que _safe typing_ and _correctness_ son indispensables para el desarrollo en aplicaciones que impactan el sector público.

### Trabajos en paralelo
Otros proyectos en los que también estamos trabajando : 
 - Bajo nivel: No me refiero a que es despreciado, simplemente me refiero a Sistemas embebidos, que tal vez implementemos con C/C++, tal vez Rust
 - Apoyo social a la comunidad: Regresar algo, siempre ha sido una motivación personal y es un punto importante que estamos tratando de impulsar aquí en MCITCSA, siempre con la tecnológica de la mano.
 - Consultoría en procesos de negocios: Uno de los _main core_ o principales puntos de la empresa. Este punto lo abordaré con más detalle cuando tenga más experiencia con clientes y con las implementaciones de los sistemas a mayor escala.

 So, that happened... Ahora me dedico a darle un poco más de dinamismo a una pequeña empresa que había quedado un poco letárgica. Pero no por eso me voy a dormir en mis laureles, en los siguientes meses escribiré más a detalle sobre lo que hemos trabajado aquí en **MCITCSA**.