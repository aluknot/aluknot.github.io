---
layout: project
title:  "Web Laureano Miceli"
date:   06-12-2014 16:54:46
author: Laureano Miceli
categories:
- proyecto
img: portfolio_01.jpg
thumb: thumb01.jpg
carousel:
- laureano01.jpg
- laureano02.jpg
client: proyecto propio
website: http://aluknot.github.io/laureano
tags: html5, css3, jquery, semantic-ui, firebase
---
####PROYECTO WEB PERSONAL
Esta es mi web personal anterior, la desarrolle hace unos pocos meses y le di el toque final hace unos dias. Sin embargo decidi usarla solamente como un trabajo a mostrar y termine decantandome por usar la web actual como mi web personal y portfolio, ya que no quede del todo conforme con su desarrollo, en el transcurso del mismo aprendi nuevas tecnologias y mejores formas de implementarlas. Aparte mi idea era implementarle un blog y para ello decidi instalar [Jekyll][jekyll], un sistema que actua como si fueran paginas dinamicas siendo estaticas, con lo cual se puede utilizar dentro de [GitHub][github] (donde solo soporta contenido estatico). Por ende la web en la que te encontras en este momento corre bajo Jekyll. 

####Desarrollo
La web fue realizada en HTML5/CSS3 como base, y se le implemento algo de Javascript para un cambio de pagina dinamico en el boton "¿Quien Soy?", para los diferentes links que abren modals en pantalla, para el pequeño formulario de suscripcion y para el conteo de links de cada trabajo realizado. A su vez se utilizo [FireBase][firebase] como base de datos, tanto para el guardado de emails suscriptos como para la cantidad de clicks almacenados.

En conjunto con todo ello se hizo uso de [Semantic-UI][semanticui] (un framework de CSS), jQuery y [Gulp][gulp] para la reduccion de tamaño en los archivos de Javascript, CSS y HTML, minificandolos para aumentar el rendimiento a la hora de descargar y navegar la web. 

[jekyll]: https://github.com/jekyll/jekyll
[github]: https://github.com
[firebase]: https://www.firebase.com
[semanticui]: semantic-ui.com
[gulp]: gulp.io