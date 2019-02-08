# README

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


## Modelo

Al generar un modelo invocamos directamente a la base de datos.

Los modelos se definen en singular. La clase mapea un solo elemento en la base de datos.

`model/user.rb`
`model/nombre_tabla.rb`

`$`

Crea una tabla users en la base de datos y la mapea como una clase de ruby

Los modelos funcionan junto con las migraciones(migrate), es el encargado de crear o alterar una tabla en la base de datos.

Para que una migración pueda cumplir con la tarea de alterar la base de datos debemos correr el comando:

`rake db:migrate`

## Probar migraciones

Para probar nuestras migraciones a traves de la consola con Active Record:

`rail c`

### Active Record

Es un lenguaje de ruby, para poder hacer consultas mas sencillo que con SQL. Puede editar, crear o eliminar recuros.
