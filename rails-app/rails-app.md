!SLIDE subsection

# Rails App #

!SLIDE commandline

# Install rails #

    $ gem install rails

!SLIDE commandline

# Create a rails app #

    $ rails new to_do

      create  README
      create  Rakefile
      ...
      create  vendor/plugins/
      create  vendor/plugins/.gitkeep

!SLIDE commandline

# Launch the site

    $ cd to_do
    
    $ rails s

!SLIDE code

    .
    ├── app
    │   ├── models
    │   ├── views
    │   ├── controllers
    │   └── ...
    ├── config
    ├── db
    │   └── migrate
    ├── public
    │   ├── images
    │   ├── javascripts
    │   └── stylesheets
    └── ...

!SLIDE commandline

# Project Scaffolding

    $ rails g scaffold Project name:string

      create    db/migrate/20110627160358_create_projects.rb
      create    app/models/project.rb
      ...
      route  resources :projects
      ...
      create    app/controllers/projects_controller.rb
      ...
      create      app/views/projects
      create      app/views/projects/index.html.erb
      create      app/views/projects/edit.html.erb
      create      app/views/projects/show.html.erb
      create      app/views/projects/new.html.erb
      create      app/views/projects/_form.html.erb
      ...
      create    public/stylesheets/scaffold.css
      ...

!SLIDE commandline

# Run migrations! #

    $ rake db:migrate

      ==  CreateProjects: migrating =================================================
      -- create_table(:projects)
         -> 0.0026s
      ==  CreateProjects: migrated (0.0027s) ========================================

    Creates a table with 4 fields: id, name, created_at & updated_at


!SLIDE bullets

# Interact with your projects #

* `rails s`
* localhost:8080/projects
* Create 3 projects.

!SLIDE code

## db/migrate/...projects.rb ##

    @@@ ruby
    class CreateProjects < ActiveRecord::Migration
      def self.up
        create_table :projects do |t|
          t.string :name

          t.timestamps
        end
      end

      def self.down
        drop_table :projects
      end
    end

!SLIDE code

## app/controllers/projects_controller.rb ##

    @@@ ruby
    class ProjectsController < ApplicationController

      index, show, new, create
      edit, update, & destroy

    end

!SLIDE code

## app/views/projects/ ##

    .
    ├── edit.html.erb
    ├── _form.html.erb
    ├── index.html.erb
    ├── new.html.erb
    └── show.html.erb

!SLIDE code

## config/routes.rb ##

    @@@ ruby
    Todo::Application.routes.draw do
      resources :projects
    ...
    end


## app/models/project.rb ##

    @@@ ruby
    class Project < ActiveRecord::Base
    end

!SLIDE code

## Validations ##

    @@@ ruby
    class Project < ActiveRecord::Base
      validates_presence_of :name
      validates_uniqueness_of :name
    end

!SLIDE commandline

# Task scaffolding

    $ rails g scaffold Task name:string project_id:integer done:boolean
    ...
    $ rake db:migrate


!SLIDE code

# belongs_to & has_many #

    @@@ ruby
    # app/models/project.rb
    class Project < ActiveRecord::Base
      ...
      has_many :tasks
    end

    # app/models/task.rb
    class Task < ActiveRecord::Base
      belongs_to :project
    end

!SLIDE code

# before_filter #

    @@@ ruby
    # app/controllers/tasks_controller.rb

    class TasksController < ApplicationController
      before_filter :calculate_projects

      private

      def calculate_projects
        @projects = Project.all
      end
    end

!SLIDE code

# before_filter #

    @@@ ruby
    # app/controllers/tasks_controller.rb

    class TasksController < ApplicationController
      before_filter :calculate_projects,
        :except => :index

      private

      def calculate_projects
        @projects = Project.all
      end
    end

!SLIDE code

# Statuses #

    @@@ ruby
    # app/views/tasks/_form.rb

    <%= f.text_field :status %>

    # change that to this VVVVVV

    <%= f.collection_select :status, Task::STATUSES,
        :to_s, :to_s, :include_blank => true
    %>


!SLIDE code

# Statuses (II) #

    @@@ ruby
    # app/views/tasks/_form.rb

    <%= f.text_field :status %>

    # change that to this VVVVVV

    <%= f.collection_select :status, Task::STATUSES,
        :to_s, :to_s, :include_blank => true
    %>




