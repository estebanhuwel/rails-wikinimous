# README
1 -------------------------------------------
A------------- MODELO
  -Generamos el modelo Article por medio del generador de Rails adecuado
    title, como string
    content, como text

  -rails generate model Article title:string content:text

B------------- DB:MIGRATE
  -Cuando trate de ver la vista tuve que migrar, porque habia creado la tabla
  -por lo tanto con el comando "rails db:migrate" pude llamar la migracion


2 -------------------------------------------
A------------- SEED
  - Agrega la gema faker a tu Gemfile y corre bundle install. Usa esta gema para generar 10 artículos falsos en db/seeds.rb Cuando tu código esté listo, corre lo siguiente
  - Getting Started
      -- Start by including faker in your Gemfile: gem 'faker'
      -- Then run bundle install.
      -- Write this code in seeds.db
              require 'faker'
              10.times do
                Article.create!(
                  title: Faker::Book.title,
                  content: Faker::Quote.yoda,
                )
              end

  - En la terminal escribimos --> rails db:seed

3 -------------------------------------------
CONTROLADOR
  -Generamos el controlador ArticlesController
  -rails g controller ArticlesController

4 -------------------------------------------
PROCESO DE CRECION WEB
  - definimos nuestra ruta -> get "articles", to: "articles#index"
  - vamos al cntrolador a definir la accion index
  - vamos a las vistas y generamos la vista index.html.erb


  - y luego creando la lista en nuestra vista index.html.erb, con el siguiente codigo
      ** <% @tasks.each do |task| %>
            <li><%= task.title %></li>
         <% end %>

  - como queremos crear una expansion de los detalles, tenemos que generar en nuestra vista index un link_to, con eso vamos directamente a lo que serian nuestro elemento solo
      ** <% @tasks.each do |task| %>
            <li><%= link_to task.title, task_path(task.id) %></li>
         <% end %>

  - nos falta la ruta que creamos por medio de este codigo
      ** get "tasks/:id", to: "tasks#show", as: :task
