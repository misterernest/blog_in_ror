# RUBY ON RAILS (RoR)

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version
  `2.4.1`
* System dependencies
  `Bundler 2.1.1`
* Configuration
  `Rails 5.1.5`
* Database creation
  `gem 'pg', '>= 0.18.4', '< 2.0'`
* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## PATRON MODELO, VISTA Y CONTROLADOR.
### MVC

### MODEL -> VIEW -> CONTROLLER

![MODEL - VIEW - CONTROLLER](https://github.com/misterernest/blog_in_ror/blob/master/mvc-sequence.gif?raw=true)

***VIEW: lo que el cliente ve.***
***MODEL: el manejo de datos en la base de datos***
***CONTROLLER: La logica de negocio***
 ***ROUTES: Direcciona al navegador hacia donde dirigirse, según la solicitud del navegador o de una vista***

## Scaffold

`rails g scaffold tasks task:string`

Es el comando que nos permite crear el modelo, la vista y el controlador en un solo paso, con metodos REST definidos, en un solo paso.

*NOTA: Recuerda que siempre que crees un Modelo, una migración o un Scaffold, deberás actualizar tu esquema corriendo el comando:*

`rake db:migrate`

## Modelo

Al generar un modelo invocamos directamente a la base de datos.

Los modelos se definen en singular y con la primera letra en mayuscula. La clase mapea un solo elemento en la base de datos.

`model/Article.rb`
`model/Nombre_tabla.rb`

`$ rails g model Article title:string body:text user:references`

Crea una tabla `Article` en la base de datos y la mapea como una clase de ruby.

Ademas le crea un atributo `title` de tipo `string`
y atributo `body` de tipo `text`

Y el `user:references` agrega un `belong_to:user` al archivo `article.rb`

### Migraciones

Los modelos funcionan junto con las migraciones(migrate), es el encargado de crear o alterar una tabla en la base de datos.

Un comando así:

`$ rails g migration AddNameToUser name:string`

Crear una migración llamada `AddNameToUser` con un nuevo campo llamado `name` de tipo `string`.

Algo así:

```
class AddNameToUser < ActiveRecord::Migration[5.2]
  def change
    add_column :users, :name, :string
    end
end
```

Para que una migración pueda cumplir con la tarea de alterar la base de datos debemos correr el comando:

`rake db:migrate`

### Probar migraciones

Para probar nuestras migraciones a traves de la consola con Active Record:

`rail c`

### Active Record

Es un lenguaje de ruby, para poder hacer consultas mas sencillo que con SQL. Puede editar, crear o eliminar recuros.

### SEEDS

El archivo seed, nos sirve para sembrar datos dentro de nuestra base de datos.

Es un pequeño bloque de array

```
# ruby encoding: utf-8
article_list = [
  [ "¿Cómo hacer videojuegos?", "Seguramente ya has escuchado que la industria de los videojuegos tuvo el doble de ganancias que Hollywood en 2017. La industria de los videojuegos viene pisándole los talones a la gran pantalla desde desde el 2013, y podrías creer entonces que crear tu propia empresa de videojuegos es el futuro, pero la realidad es que hacer un videojuego no es fácil.", 1 ],
  [ "Cuatro formas de implementar tecnología en tu empresa", "La tecnología es una gran aliada de la comunicación en el proceso de Transformación Digital. Tanto para la comunicación interna como externa, puedes elegir una herramienta que responda a las necesidades que tiene tu equipo y centralizar la información y comunicación en ella.", 1 ],
  [ "Cómo automatizar y optimizar tu trabajo en NodeJS y Grunt", "No basta con seguir los pasos de esta guía: te invito a probar, evaluar y jugar con las posibilidades. Tu mejor escuela es la práctica. Con el tiempo verás que tienes en tus manos una gran herramienta.", 1 ],
  [ "Tres tips infalibles para aprender inglés online", "Durante muchos años he escuchado que aprender un idioma es una de las metas para iniciar un nuevo año, y el idioma más destacado de todos es el inglés. Pero, ¿cómo aprenderlo de la forma más efectiva y sobre todo que sea flexible? A lo largo de estos años he encontrado que un gran porcentaje de las personas que lo aprendieron, buscaron un método online ????.", 1 ]
]
```
Que se itera, con un codigo así:

```
article_list.each do |title, body, user_id|
  Article.create( title: title, body: body, user_id: user_id )
end
```

Gracias al poder de ActiveRecord se crean registros dentro de la base de datos, con `title`, `body` y `user_id`.

y con el comando:

```
rails db:seed
```
Se crean los seed dentro de la base de datos.

*Las SEED funcionan para tener datos dentro de la base de datos y así poder realizar las pruebas correspondiente.*

Siempre puedes consultar datos dentro de la consola `rails c`

con el comando `nombre_modelo.all` algo así como: `Article.all`, para visualizar todos los recuros que tienes en la tabla articulos.

Otro comandos desde `rails c` (con la tabla article), son:

El primer registro de la tabla article
```
Article.first
```
el ultimo elemento de la tabla article
```
Article.last
```
El elemento de article con id 3
```
Article.find(3)
```
trae el article con titulo (`title`) '¿Cómo hacer videojuegos?'
```
Article.where(title: ‘¿Cómo hacer videojuegos?’).first
```


## CONTROLLER

Para crear un controlador llamado `pages` (en minuscula y en plural) con dos metodos: `index` y `contact`, los metodos se convierten en las vistas para este recurso, `pages`, ademas de la rutas de cada vista.

Es el siguiente comando:
```
$ rails g controller pages index contact
```

Los controladores se crean en minuscula y singular.

## VIEW
