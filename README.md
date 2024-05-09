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

Si no queremos tener que escribir cada detalle del xml del RSS, podemos utilizar feedparser, que leerá el RSS de la página que queramos (la vanguardia en este caso) y nos sacrá la información que necesitemos. Podemos acceder a los elementos del canal (<channel>) que se encuentran en d.entries (es una lista).
También podemos acceder a los items de cada elemento con las palabras clave linmk, description o published. 


## Cómo utilizar nuestra aplicación

Para usar nuestra aplicación deberemos iniciar flask, que nos proporcionará un enlace que deberemos pinchar. A partir de ahí se nos mostrará nuestro index.html, nuestra página principal de la aplicación. Nosotros podremos usar la aplicación tanto en remoto (con la función de auto refresco), como en local. Esto último lo hacemos modificando el index.html para añadir también nuestra nueva sección y el enlace al XML que habremos descargado en nuestro ordenador y tendremos guardado en nuetra carpeta del proyecto.


# TBC (To Be Continued)