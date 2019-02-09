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


## CONTROLLER

Para crear un controlador llamado `pages` (en minuscula y en plural) con dos metodos: `index` y `contact`, los metodos pueden venir siendo las vistas para este recuro, `pages`

Es el siguiente comando:
```
$ rails g controller pages index contact
```

Los controladores se crean en minuscula y singular.

## VIEW
