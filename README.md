# Proyecto FLask

## Desplegar el entorno virtual

Para trabajar en este proyecto vamos a crear un entorno virtual, en el que instalaremos algunas cosas que nos harán falta para trabajar. Abriremos el terminal del IDE y procederemos 

1. Ejecutamos el comando ```python -m venv .venv```
Con este comando crearemos el entorno virtual en si.
2. A continuación activamos el entorno virtual con ```.venv\Scripts\activate```
Ya tenemos nuestro entorno virtual creado y activado, por lo que ahora podemos proceder a instalar las cosas que nos serán necesaris para el proyecto, flask y feedparser.

## Trabajar con Flask 
Una vez dentro del entorno virtual deberemos iniciar Flask ejecutando el código ```flask run --debug```, y si necesitamos parar el servidor Flask, hacemos ctrl + C como cuando paramos ejecuciones en la terminal.

## Jinja y las plantillas
Jinja es un gestor de plantillas ampliamente usado por desarroladores de Python. Se usa para crear formatos de lenguaje de marcas que le devolvemos al usuario. Para que Jinja interprete una plantilla debe estar dentro de una carpeta que, forzosamente, debe llamarse _templates_.
Las plantillas de Jinja soportan el sistema de herencia por el que una plantilla puede heredar aspectos de otra plantilla. Es muy útil si nos paramos a pensar que la mayoría de webs tienen un layout similar en todas sus páginas, si no exactamente igual. Podemos crear una plantilla base en la que ponemos lo más básico, y después aplicar esa base a otras páginas, a parte de las plantillas específicas de cada página, como puede ser un error 404.
## Estructura de una app con Flask
Necesitamos especificar una estructura para nuestra aplicación porque así podremos mantener el código limpio, ordenado y accesible. Como hemos mencionado, Jinja buscará una carpeta llamada templates, que espera que esté creada al mismo nivel que encontramos el app.py.

## Renderizar plantillas
En el documento app.py podremos renderizar las plantillas para mostrarlas en nuestra página. Para crear nuestro documento podremos utilizar variables dinámicas que le pasaremos a nuestra función ``render_template()``. Renderizar es, en esencia, rellenar las variables que hemos utilizado con los datos que le pasamos a render_template().

## Qué es el RSS
Es un acrónimo para Really Simple Syndication. Está escrito en XML, y es un feed que te permite recoger noticias de maneral local o en línea para tener una interfaz de lectura de datos más sencilla y concisa. El RSS se usa para mantener al día a las personas que lo usen, por eso se suele usar mucho en las listas de correo. Se necesita un lector que lo procese, o si no veremos únicamente un XML como puede pasar con Firefox, donde hay que activar el lector de RSS. 

## Cómo crear un RSS
Como ya hemos mencionado, se escribe típicamente en XML. Abriremos una etiqueta <rss version= ""> en la que encapsularemos todo el trabajo.
En el primer nodo (<channel>) deberemos declarar el canal, el título del canal, los links de la página, una descripción del feed y el idioma en el que está. Esta parte será estática. 
Una vez tengamos esto necesitaremos crear un nuevo nodo <item>, que cambiará cada vez que se actualicfe la página ya que se añade un nuevo nodo. En este nodo añadiremos el titulo, la fecha de publicación, el autor y una descripción. 

## RSS y feedparser

Si no queremos tener que escribir cada detalle del xml del RSS, podemos utilizar feedparser, que leerá el RSS de la página que queramos (la vanguardia en este caso) y nos sacará la información que necesitemos. Podemos acceder a los elementos del canal (<channel>) que se encuentran en d.entries (es una lista).
También podemos acceder a los items de cada elemento con las palabras clave link, description o published. 


## Cómo utilizar nuestra aplicación

Para usar nuestra aplicación deberemos iniciar flask, que nos proporcionará un enlace que deberemos pinchar. A partir de ahí se nos mostrará nuestro index.html, nuestra página principal de la aplicación. Nosotros podremos usar la aplicación tanto en remoto (con la función de auto refresco, se puede cambiar de modo comentando/descomentando esa parte en el código en el archivo app.py, lo podemos encontrar al final del archivo), como en local. Esto último lo hacemos modificando el index.html para añadir también nuestra nueva sección y el enlace al XML que habremos descargado en nuestro ordenador y tendremos guardado en nuetra carpeta del proyecto.


## Cómo utilizar Bootstrap
En este proyecto hemos utilizado el framework bootstrap, que podemos usar de manera local si descargamos las librerías de utilidades, aunque yo he preferido usar los CDN, o sea, los links de la red de distribución de contenido que hace que podamos usar bootstrap de manera remota. Esto tiene un inconveniente, puesto que si utilizamos la aplicación en modo local y sin internet, no podremos usar bootstrap. Yo he optado por esta opción en base al tiempo del que yo disponía.

Bootstrap funciona mediante clases, en las que puedes especificar cómo quieres que se comporte el objeto al que le estás añadiendo las clases. Bootstrap detecta las clases de manera automáticamente y aplica un css "pre-hecho" a la misma.

Bootstrap cuenta con una distribución de columnas que podemos manejar y editar a nuestro gusto en base a si vamos a ver el contenido en una pantalla más o menos grande. Cuando usamos las columnas, no tenemos que hacer 12 columnas de manera obligatoria, sino que podemos repartir el espacio entre las columnas que queramos especificando el tamaño de pantalla y las columnas que queremos. Por ejemplo:
 
```col-xs-12```

Esto signficará que nuestra columna ocupará todo el espacio disponible en una pantalla extra pequeña, o sea, que en una pantalla muy pequeña sólo veremos una columna. 
Podemos "amontonar" las especificaciones de columnas para diferentes tipos de pantalla, es decir:

``col-sm-6 col-md-4 col-lg-3``

Esto significa que en una pantalla pequeña el espacio se dividirá en dos columnas que ocuparás 6 "minicolumnas" de bootstrap, en una pantalla mediana habrá 3 columnas porque cada columna ocupará 4 "minicolumnas" y en una pantalla grande tendremos 4 columnas porque cada columna ocupará 3 "minicolumnas".

En la documentación oficial de Bootstrap tenemos muchos ejempolos de las funcionalidades que nos ofrece. Para más información: 
https://getbootstrap.com/docs/5.3/getting-started/introduction/

## Editar los valores por defecto de Bootstrap

Existen varias maneras de sobreescribir los valores por defecto de boostrap, uno de ellos es editar el archivo sass y recompilarlo enun archivo css. Existe una extensión de visual studio que hace esta tarea más fácil. En mi caso no he optado por esta opción ya que consideré que con el tiempo y disponibilidad que tenía no podría hacerlo de la manera "correcta".
Otra forma es, en tu propio archivo css marcar una propiedad como "importante", por ejemplo:

```Font-family: 'Roboto', sans-serif !important;```

Esta no es la mejor manera, pero es más "sencilla" si no tenemos demasiado tiempo.
En mi caso esa forma no estaba funcionando del todo, así que opté por la última, que no es recomendada si vas a publicar una aplicación de manera oficial, pero en entorno escolar considero que se puede usar sin más problema. 
La última opción es sobreescribir los valores de las variables de bootstrap declarando los valores en root en el archivo css y usando el nombre de valor para cambiar el contenido. 
Es decir, en la cabecera de tu archivo css escribres:

``` :root{*nombre del valor a cambiar*} ```

Por ejemplo, yo quería cambiar la fuente de la aplicación, pero la opción de marcar como importante por lo que utilicé la opción de sobreescribir en la raiz el tipo de fuente con `` --bs-body-font-family: 'Inconsolata', sans-serif;``. También importé la fuente desde google fonts para que funcionase.

## Cosas extra

Una de las cosas que se pedían era hacer un carousel. Debido al layout que yo quería utilizar, no podía poner los carrousels tal cual porque no estaban respondiendo bien a la ubicación que les estaba dando, al igual que las fotos de las noticias.
Para solucionar esto he usado las cartas de bootstrap, que me han permitido meter dentro las imágenes/carrousel sin problemas más allá de que se ve un poco la card por debajo ya que tengo las esquinas de las imágenes redondeadas. 

Para añadir iconos intenté usar iconos de Font-awesome como se recomendaba, pero no me estaban funcionando, no sé si por la versión (probé con las dos), así que finalmente decidí utilizar los iconos en formato png de flaticon, por lo que a continuación pondré los respectivos créditos:

<a href="https://www.flaticon.com/free-icons/bee" title="bee icons">Bee icons created by Freepik - Flaticon</a>

<a href="https://www.flaticon.com/free-icons/war" title="war icons">War icons created by noomtah - Flaticon</a>

<a href="https://www.flaticon.com/free-icons/politics" title="politics icons">Politics icons created by Uniconlabs - Flaticon</a>

<a href="https://www.flaticon.com/free-icons/gym" title="gym icons">Gym icons created by dDara - Flaticon</a>

<a href="https://www.flaticon.com/free-icons/theatre" title="theatre icons">Theatre icons created by Freepik - Flaticon</a>

Para tener un poco más claro el uso de bootstrap he visto varios videos:

Video sobre sómo añadir bootstrap:
https://www.youtube.com/watch?v=qeS3rOa8voU

Video sobre el sistema de grid:
https://www.youtube.com/watch?v=qeS3rOa8voU

Video sobre las clases de Bootstrap:
https://www.youtube.com/watch?v=nCeHeA7IsvU&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=5

Video sobre las cards:
https://www.youtube.com/watch?v=NRoET8-8cbw&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=10

Video sobre acordeones:
https://www.youtube.com/watch?v=cVThXv6hYW0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=11
Tenía intención de hacer acordeones pero me quedé sin tiempo solucionando otros problemas, así que al final no los añadí.

## Trabajar con amor
Le he puesto mucho cariño Juan, espero que se note ;)