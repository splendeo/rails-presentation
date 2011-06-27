!SLIDE subsection

# Rails #

!SLIDE bullets

# Concepts #

* Model
* View
* Controller
* Migration
* Route
* Scaffolding


!SLIDE bullets

# Model #

* ~ db information + business logic
* Usually mapped to a db table
* Employee, Company, Player, Article
* Located in `app/models`

!SLIDE bullets

# View #

* ~ html + css; user interface
* Reusability: helpers and layouts
* Connected to the controller
* Located in `app/views`

!SLIDE bullets

# Controller #

* ~ CRUD actions on models
* Sends / receives information from views
* `params` variable => hashed parameters
* Located in `app/controllers`

!SLIDE bullets

# Migration #

* Ruby code that modifies the DB structure
* Controlled via the `rake db:xxx` commands
* Located in `db/migrate`

!SLIDE bullets

# Routes #

* Translates urls into controller actions
* Located in `db/config/routes.rb`


!SLIDE bullets

# Scaffolding #

* Boilerplate MVC+migration code
