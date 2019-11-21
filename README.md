# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* Steps
1. Install the following gems ...

2. Run guard init
```sh
$ guard init livereload
```
3. Then we need to execute guard via bundle like this:
```sh
$ bundle exec guard
```
4. Now we need to generate the instalation of simple forms like this:
```sh
$ rails generate simple_form:install
```
5. Next step is to generate the instalation of divise with the following command:
```sh
$ rails generate devise:install
```
6.  Then we need to config devise
```sh
# /config/enviroments/development.rb

Rails.application.configure do
	.
	.
	.
  # devise
  config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
end

```
7. After the divise configuration we need to change our application.html.erb
```sh
<!DOCTYPE html>
<html>
  <head>
    <title>DribbbleClone</title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>
    <meta name="viewport" content="with=device-width, initial-scale=1">

    <%= stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= stylesheet_link_tag "https://maxcdn.bootstrapcdn.com/font-awsome/4.7.0/css/font-awesome.min.css" %>
    <%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>
  </head>

  <body>
    <% if flash[:notice] %>
      <div class="notification is-primary global-notification">
        <p class="notice"> <%= notice %> </p>
      </div>
    <% end %>
    <% if flash[:alert] %>
      <div class="notification is-denger global-notification">
        <p class="alert"> <%= alert %> </p>
      </div>
    <% end %>
    
    <%= yield %>
  </body>
</html>
```
8. then we generate a controller for home index with the following command:
```sh
$ rails generate controller home index
```
9. Now in your routes.rb file we need to look it like this:
```sh
Rails.application.routes.draw do
  root 'home#index'
  # For details on the DSL available within this file, see https://guides.rubyonrails.org/routing.html
end
```
10. Testing if the rails server is running just go to your browser and type localhost:3000 and you will see the following:
```sh
Home#index
Find me in app/views/home/index.html.erb
```
11. If you are not running the server go and fireup the server with :
```sh
$ rails server
```
12. Check step 10 to see if we see that output in the browser
13. Then we need to generate the views for devise, please do the following command:
```sh
$ rails generate devise:views
Running via Spring preloader in process 7043
      invoke  Devise::Generators::SharedViewsGenerator
      create    app/views/devise/shared
      create    app/views/devise/shared/_error_messages.html.erb
      create    app/views/devise/shared/_links.html.erb
      invoke  simple_form_for
      create    app/views/devise/confirmations
      create    app/views/devise/confirmations/new.html.erb
      create    app/views/devise/passwords
      create    app/views/devise/passwords/edit.html.erb
      create    app/views/devise/passwords/new.html.erb
      create    app/views/devise/registrations
      create    app/views/devise/registrations/edit.html.erb
      create    app/views/devise/registrations/new.html.erb
      create    app/views/devise/sessions
      create    app/views/devise/sessions/new.html.erb
      create    app/views/devise/unlocks
      create    app/views/devise/unlocks/new.html.erb
      invoke  erb
      create    app/views/devise/mailer
      create    app/views/devise/mailer/confirmation_instructions.html.erb
      create    app/views/devise/mailer/email_changed.html.erb
      create    app/views/devise/mailer/password_change.html.erb
      create    app/views/devise/mailer/reset_password_instructions.html.erb
      create    app/views/devise/mailer/unlock_instructions.html.erb
```
14. With the devise setup now we can generate the devise user model with the following command:
```sh
$ rails generate devise User
Running via Spring preloader in process 7141
      invoke  active_record
      create    db/migrate/20191121005623_devise_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
      insert    app/models/user.rb
       route  devise_for :users
```
15. With the devise User model generated we can proceed to do the migration with the following command:
```sh
$ rails db:migrate
== 20191121005623 DeviseCreateUsers: migrating ================================
-- create_table(:users)
   -> 0.0024s
-- add_index(:users, :email, {:unique=>true})
   -> 0.0017s
-- add_index(:users, :reset_password_token, {:unique=>true})
   -> 0.0013s
== 20191121005623 DeviseCreateUsers: migrated (0.0056s) =======================
```
16. Now we need to edit routes.rb file like this:
```sh
Rails.application.routes.draw do
  devise_for :users, controllers: { registrations: 'registrations' }
  .
	.
	.
end
```
17. 21:31



