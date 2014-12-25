---
layout: post
title: "Dale acceso a tu localhost desde cualquier otra pc via internet"
date: 25-12-2014 06:24
author: Laureano Miceli
img: post02.jpg
thumb: default.jpg
shortUrl: http://adf.ly/vXqrv
etiquetas:
- tutorial
- ngrok
- localhost
categories:
- blog
- tutoriales
- otros
---

A la hora de desarrollar una web, instalar algun sistema prefabricado o cual sea tu caso y necesites mostrarle a otra persona lo que estes haciendo. Primero si estas trabajando con lenguajes _backend_ del lado del servidor como PHP, vas a necesitar montar tu servidor con [XAMPP][1] u algun otro similar. Teniendo en cuenta que ya estas familiarizado con dicho paquete y que tengas ya tu **localhost** funcionando como servidor web (en el caso de que no lo estes, hay mucha informacion en internet, buscando por [Google][2] o mismo videotutoriales en [Youtube][3] al respecto). Lo siguiente seria lograr que tu localhost pueda ser accesible por otras PCs, ya que el **localhost** es lo mismo que ir a **127.0.0.1** lo cual es tu IP local a la que solo vos podes acceder. <!--more-->

Para lograr esto hay varias alternativas llamadas "tuneles", tenemos a [PageKite][4], [Forward][5], [ProxyLocal][6], [BrowserStack][7] y [ngrok][8], aunque probablemente haya mas opciones estas son por las que me cruce en dicha busqueda.

# Alternativas

---

Voy a dar una breve descripcion de las distintas alternativas, muy por encima. Para que tengas un panorama de las distintas opciones, sin embargo yo me decante por usar **ngrok** por lo que si no te interesan estas descripciones podes salteartelas e ir un poco mas abajo.

- **PageKite**: La use un tiempo, tiene funciones avanzadas que por lo menos en mi caso no utilice. Esta desarrollada en Python por lo que lo tenes que tener instalado en tu PC (Python 2.7 en adelante). Tiene soporte para Windows, Mac OS X, Linux y hasta para Android. Es utilizado bastante por parte de los que tienen servidores del juego Minecraft. Debo decir que personalmente tuve algunos problemas donde no me funcionaba, pero puede que haya sido un asunto particular mio, por lo general funciono bastante bien. De todos modos tiene una desventaja, es **gratis por 1 mes** por lo cual me decante por no utilizarla.

- **Forward**: No la utilice, por la misma razon que PageKite. En su momento era **gratis por 1 mes** pero actualmente es **gratis por 7 dias**. Se ve que la mejoraron mucho ultimamente, parece que antes era una aplicacion desarrollada en Ruby pero ahora es basicamente una extension de Chrome y con una funcionalidad muy eficaz, simple y rapida. A su vez tambien parece tener otras funciones avanzadas, incluso mucho mas amplias que PageKite... pero no me voy a meter en ello ya que es una opcion descartada, por lo menos para mi.

- **BrowserStack**: Tampoco la utilice, porque es demasiada robusta para el fin que necesite. Debe ser de las mas grandes de todas estas alternativas, es como una maquina virtual con varias funciones de testeo tanto para dispositivos grandes como para dispositivos moviles. Aparte es una herramienta bastante costosa, aunque esta la posibilidad de usarla de prueba por un tiempo como las anteriores (no se puntualmente cuanto).

- **ProxyLocal**: No la utilice, pero parece ser muy similar a ngrok. Ya que es bastante sencilla sin tantas utilidades extras, es gratis y se puede utilizar rapidamente sin perder tiempo. Eso si, la herramienta esta desarrollada en Ruby por lo que requiere que lo tengas instalado en tu PC.

# ngrok

---

Personalmente me decante por esta opcion despues de haber utilizado PageKite. Es simple, sencilla y gratis, ya que lo unico que necesito es que los demas puedan acceder a mi localhost, ni mas ni menos. Esta aplicacion cuenta con soporte para Windows, Mac OS X y Linux.

En su uso mas basico no requiere ni siquiera registracion (al igual que ProxyLocal), sin embargo si queres mayor funcionalidad podes optar por registrarte. Y si aun no estas satisfecho tambien podes pagar para agregarle mayores caracteristicas al servicio.

Ya explicado todo, voy a explicarte como utilizarlo, es realmente muy sencillo. Primero vamos al [sector de descargas][9] de su web para descargar la aplicacion de acuerdo a nuestro sistema operativo, en mi caso es Windows y los procedimientos siguientes van a ser puntualmente explicados para esta plataforma. Al bajarlo va a venir comprimido en .zip, lo descomprimis con la herramienta que utilices (en mi caso [7zip][10]) y al archivo descomprimido llamado **ngrok.exe** lo debes mover al destino donde se encuentra tu web, la cual queres que sea accesible desde otra pc. En mi caso al utilizar XAMPP seria en `C:\xampp\htdocs\MiProyecto`

Ahora solo basta con abrir una terminal de comandos (que puede ser la que viene por defecto en windows o alguna que utilices como Git Bash que es genial) y dirigirte por medio del comando `cd <destino>` a la carpeta mencionada anteriormente donde colocaste el archivo **ngrok.exe**. Sin embargo te voy a dar un pequeño tip util para lograr esto sin tener que hacer uso del comando `cd`. Abris la carpeta de destino y manteniendo `SHIFT` haces click derecho en algun lugar vacio dentro de la misma y se te va a habilitar la opcion de **Abrir ventana de comandos aqui** por lo que se te va abrir la terminal de comandos directamente en ese destino.

Ahora solo nos queda escribir `ngrok 80` y darle enter. Nos va a generar el tunel como se ve en la siguiente imagen:

![Datos devueltos por ngrok en la terminal de comandos]({{ site.url }}/assets/img/blog/post02/ngrok_cmd.jpg)

Donde nos va a dar el link a nuestro localhost, que obviamente puede ser accesible por medio de otra PC. A su vez contamos con una herramienta muy util dirigiendonos a [http://localhost:4040][14] con una interfaz web para visualizar las entradas que se realizan a nuestro localhost por medio del tunel que nos provee ngrok. 

Si necesitas mas funcionalidad, especialmente el poder cambiar el nombre del subdominio, entre otras mas. Podes [registrarte en la web][11] de ngrok. Al registrarte vas a tener acceso a un **token** que se te va a dar como codigo unico, algo asi como `3k1N6pvL+2hu0FKtKSOj`. Se usa con el comando `-authtoken` y no es necesario ponerlo todas las veces que utilices ngrok, con hacerlo la primera vez queda guardado en tu PC para posteriores usos.

Entonces digamos que queres que se acceda a tu localhost por medio de `miweb.ngrok.com`. Simple, escribimos lo siguiente: `ngrok -authtoken 3k1N6pvL+2hu0FKtKSOj -subdomain miweb 80` le damos enter y listo (recuerden poner el authtoken solo la primera vez). Otra funcionalidad bastante util es la de `-httpauth "usuario:contraseña"` para que solo puedan acceder las personas a las que les demos los datos de usuario y contraseña.

# Dato Extra

---

Esto es un caso muy particular que me sucedio a mi al utilizar el sistema [PrestaShop][12] pero aun asi te lo comento por las dudas, porque te puede pasar con algun caso similar utilizando algun otro sistema.

Cuando yo les daba a los demas mi link generado por ngrok pasaba que automaticamente los redirigia al localhost, pero no al mio... sino al de ellos. Por ende les arrojaba un error tipico de falla de conexion y no podian acceder a mi tienda, cuando en realidad si estaban accediendo a ella... solo que automaticamente eran redirigidos a `localhost`. El problema estaba en que sistemas de este tipo, en las configuraciones del mismo te piden que coloces la URL de tu web. Y en mi caso claramente era `localhost` por lo que a todos los redireccionaba para ese lado.

En el caso de **PrestaShop 1.6** se tienen que dirigir dentro del _Panel de Administracion_ a **Preferencias > SEO + URL** y dentro de ahi modifican los datos que figuran en el siguiente segmento:

![Sector de PrestaShop para modificar URL]({{ site.url }}/assets/img/blog/post02/prestashop_url.jpg)

Cambian `localhost` por `miweb.ngrok.com` o cualquiera sea su nuevo link de ngrok.

# Dato Extra 2

---

XAMPP tiene la posibilidad para que se pueda acceder al localhost por medio de internet, pero he intentado de todo en su momento y nunca me funciono, vaya a saber porque. De todos modos para mi estas alternativas son geniales y son independientes ya que no requieren puntualmente del uso de XAMPP, solo en casos donde se requiera de un servidor web que albergue Apache, Mysql y demas. A su vez tambien esta la opcion de [Vagrant][13], que parece ser que en sus ultimas versiones agregaron la funcionalidad esta. Nunca utilice **Vagrant** pero es algo que tengo pendiente, en un futuro seguro haga algun post al respecto.

---

Espero que les haya servido, y cualquier consulta, duda o error que haya tenido en el articulo no duden en avisarme. Saludos!

> A la hora de dar informacion respecto a las diferentes alternativas utilice como referencia la siguiente fuente: [SitePoint][15] aunque algunos datos estaban desactualizados como en el caso de Forward

[1]: https://www.apachefriends.org/es/index.html
[2]: https://www.google.com.ar/?gfe_rd=cr&ei=vA-cVNLeNcuB8Qe-_4DwDA&gws_rd=ssl#q=montar+servidor+web+xampp+-youtube
[3]: https://www.youtube.com/results?search_query=montar+servidor+web+xampp
[4]: https://pagekite.net/
[5]: https://forwardhq.com/
[6]: http://proxylocal.com/
[7]: http://www.browserstack.com/
[8]: https://ngrok.com/
[9]: https://ngrok.com/download
[10]: http://www.7-zip.org/
[11]: https://ngrok.com/user/signup
[12]: http://www.prestashop.com/es/
[13]: https://www.vagrantup.com/
[14]: http://localhost:4040
[15]: http://www.sitepoint.com/accessing-localhost-from-anywhere/