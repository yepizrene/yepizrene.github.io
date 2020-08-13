---
layout: post
title: "Empezando con GitHub Pages"
date: 2017-01-17 15:40:22 -0700
comments: false
categories: [GitHub, Blog, Octopress]
footer: false

---

![]({{ root_url }}/images/banners/octopress.png")

Hace tiempo que he querido comenzar un blog donde poder compartir mis ideas y proyectos de desarrollo, sin embargo, no encontraba la herramienta que se ajustara a mis necesidades perfectamente y que fuera a un bajo costo incluso nulo, pero un día navegando por internet en un blog de un desarrollador encontré información sobre cómo crear contenido con [GitHub Pages](https://pages.github.com/) GitHub Pages, yo ya había conocido un poco al respecto sin embargo la primera vez que intente hacerlo me fue fatal y no lo volví a intentar hasta ahora.
<!-- more -->

Durante mi primer intento leí algo al respecto de [Jekyll](https://jekyllrb.com/) y las plantillas liquid, sin embargo, me pareció algo muy tardado y a veces no tenemos tiempo para poder estar haciendo plantillas y plantillas para cada una de nuestras páginas, post, artículos, secciones, etc.

Sin embargo, reciente mente en el último encuentro que tuve con GitHub Pages me encontré con [Octopress](http://octopress.org/) un framework de Jekyll que nos facilita demasiado el trabajo, ya que permite crear un sitio web estático a partir de plantillas en HTML y documentos escritos en Markdown, en pocas palabras creamos un nuevo artículo lo editamos en el editor de texto de nuestra preferencia, guardamos y con unos cuantos comandos en la terminal o consola podemos generar un post y desplegar resultados en nuestro servidor.

### Características ###
* Desarrollado en ruby.
* Cuenta con plugins para Twitter, Google Analytics, Disqus y otros más.
* Una de las grandes ventajas es que son paginas estáticas por lo cual no se necesita ningún tipo de procesamiento en el servidor, haciendo de la carga una tarea mucho más fácil, veras como tu sitio vuela, acceso más rápido a tu blog.
* Otra característica es que no dependemos de una base de datos, podemos guardar nuestros artículos donde deseemos.
* Hay muchos themes disponibles para Octopress, lo que hacen de el un framework muy personalizable.
* Compatibilidad con GitHub Pages, lo que nos permite ahorrarnos el pago del hospedaje.

## ¿Como instalar? ##
Antes de comenzar es necesario tener instalado Jekyll para poder usar Octopress y para Jekyll es necesario tener instalado: 

1.	[Ruby]( https://www.ruby-lang.org/es/)
2.	[RubyGems](https://rubygems.org/pages/download)

Una vez está listo, instalamos la gema de Jekyll con `gem install jekyll`, este utiliza [Maruku](https://github.com/bhollis/maruku) por defecto, pero podemos cambiarlo por LaTex, RDiscount o Kramadown, pero recomiendo que dejen Maruku. Lo siguiente es crear nuestro blog, para el cual tenemos dos opciones, como mencione antes utilizar Jekyll directamente o el framework Octopress no obstante explicare ambos métodos, pero yo me quedo con Octopress.

## Crear blog con Jekyll
Jekyll da la posibilidad de crear la estructura de nuestro blog mediante el comando `jekyll new username.github.io` la cual nos creara la carpeta llamada username.github.io, recordemos que username es nuestro usuario u organización de GitHub. Esto genera la estructura siguiente:

~~~
.
├── _config.yml
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   └── 2013-12-18-welcome-to-jekyll.markdown
├── css
|   ├── main.css
|   └── syntax.css
└── index.html
~~~
Después podemos crear más carpetas y archivos, pero estos son los que se necesitan para empezar:

* **_config.yml:** almacena la información de configuración. Muchas de las opciones pueden especificarse desde la consola, pero es mejor describirlas en este archivo así no tenemos que recordarlas.
* **layouts:** son las plantillas [Liquid]( https://help.shopify.com/themes/liquid/basics) que se utilizan en los articulos, el layout se define en cada articulo en la información preliminar en [YAML]( http://jekyllrb.com/docs/frontmatter/) la etiqueta se utiliza para inyectar el contenido en la página web.
* **_posts:** aquí se encuentran todos los artículos que vayamos escribiendo, es importante que el formato de los archivos siga la siguiente estructura: año-mes-día-título.MARKUP. los enlaces permanentes se pueden personalizar para cada artículo, pero la fecha y el lenguaje de marcado se define solamente por el nombre del archivo.
Esta es la información esencial para empezar a crear un blog con Jekyll, para aprender mas sobre [plantillas]( http://jekyllrb.com/docs/templates/), [enlaces permanentes]( http://jekyllrb.com/docs/permalinks/), [paginación]( http://jekyllrb.com/docs/pagination/) y [plugins]( http://jekyllrb.com/docs/plugins/) puedes leer la [documentación de Jekyll]( http://jekyllrb.com/docs/home/).

## Crear blog con Octopress
Es una buena idea el no empezar desde cero creando nuestras propias plantillas HTML, CSS y javascript, para esto podemos utilizar [Octopress]( http://octopress.org/), el framework del que les he estado hablando, Octopress incluye:

* Plantilla de HTML5.
* Diseño mobile first responsive.
* Soporte para Twitter, Google Plus One, comentario DIsqus, Pinboard, Delicious y Google Analytics.
* Facil despligue usando Github Pages o Rsync.
* Temas construidos con Compass y Sass
* Un resaltado de sintaxis Beautiful Solarized

Además, hay plugins creados por Octopress o por la comunidad de Jekyll con algunas mejoras.
Para empezar con Octopress debemos tener Ruby 1.9.3 o posterior, podemos comprobarlo escribiendo en la consola `ruby --version`.  Una vez comprobado ejecutamos los siguientes comandos:

* Clonamos el repositorio:

~~~
git clone git://github.com/imathis/octopress.git username.github.io
~~~

* Instalamos dependencias:

~~~
gem install bundler
rbenv rehash  # Si usas rbenv, rehash para poder utilizar el comando bundle
bundle install
~~~

*Instalamos la plantilla por default:

~~~
rake install
~~~

## Desplegar en GitHub.
Una vez tenemos la primera versión de nuestro blog podemos desplegarlo en GitHub. Recuerda que necesitamos primero crear el repositorio con nombre `username.github.io`. Una vez que tenemos esto configuraremos nuestro clon de Octopress para poder hacer los commits en el repositorio que acabamos de crear. Para esto hay un comando el cual solicita la URL de nuestro repositorio y configura todo lo necesario para usar nuestro blog como GitHub Page.

~~~
rake setup_github_pages
~~~

Este comando hace lo siguiente:

1.	Solicita la url del repositorio (HTTP SSH).
2.	Cambia el nombre del puntero remoto de imathis/octopress de `origin` a `octopress`.
3.	Añade el repositorio GitHub Pages como ` origin`.
4.	Cambia la rama activa de `master` a `source`.
5.	Configura la url del blog de acuerdo al nombre del repositorio.
6.	Configura de una rama `master` en el directorio `_deploy` para el despliegue.
Una vez configurado el entorno para trabajar con GitHub Pages podemos previsualizar el resultado ejecutando el siguiente comando:

~~~
rake preview
~~~

Una vez nos aseguramos que todo está listo para subirlo a GitHub debemos generar contenido estático y desplegarlo:

~~~
rake generate
rake deploy
~~~

Además tenemos que subir el código fuente a del blog:

~~~
git add .
git commit -m ‘GitHub Page new’
git push origin source
~~~

## Nuestro primer post
Una vez configurado el entorno local y desplegado en GitHub llega el momento de escribir el primer post. Todos estos se encuentran en la carpeta `_post` y deben tener el siguiente formato `aaaa-mm-dd-title.MARKUP` donde `MARKUP` es la extensión del archivo, en nuestro caso será `md`. El formato del nombre es un requerimiento de Jekyll, así que tenemos que cumplirlo al pie de la letra.
En Octopress los post se ubican en `source/_posts` y podemos automatizar la creación de nuevos articulos utilizando el siguiente comando: 

~~~
rake new_post["title"]
~~~

El contenido se creara de forma automática con el formato adecuado y el motor de markup que elegimos, pero adicionalemente disponemos de todas las características de las templates liquid descritas en la documentación de Jekyll.

Podemos definir el separador del extracto usando la variable de configuración `excerpt_separator` en caso de estar usando Octopress el separador por default es : `<!--more -->`.

