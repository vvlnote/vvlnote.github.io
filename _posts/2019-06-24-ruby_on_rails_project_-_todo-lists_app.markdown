---
layout: post
title:      "Ruby on Rails project - todo-lists app"
date:       2019-06-24 20:23:11 -0400
permalink:  ruby_on_rails_project_-_todo-lists_app
---

## this is my first rails project. 
For this project, we need to implement login/signup and using 3rd party to log in, here, I use github account to log in.

learn from my mistake
1. setting up Github link in. I follow the instruction from [Devise Authentication Gide with Git Hub OmniAuth For Rails Application](https://medium.com/@salmaeng71/devise-authentication-guide-with-github-omniauth-for-rails-application-220aa52d5b82) to set up the log in via github.
   *set up the github omniAuth
	 *copy the clientID and Client secret from github to config/initializers/devise.rb in config.omniauth :github, "client ID", "client secret"
	 *create a callback_controller inherit from Devise::OmniauthCallbacksController
	 *add additonal column: provider, and uid into the users table
	 *in model : user add "omniauthable" under devise, and def a class method from_omniauth(auth), this method is called by callbacks_controller to authonticate the user from github
	 *in the login page, add the link to the github log in route
	 
After complete all the settings, and run the application, I got an error: The action 'github' could not be found for Devise::OmniauthCallbacksController
By googling this error message, I found out:
since the program still looking for the default callback controller (OmniauthCallbacksController), and not the one you specify as callbacks_controller. 
to fix this issue, you need to update the routes.rb file to make the program to refer to your callback controller.
in the routes.rb file:
devise_for: users, :controllers => {registrations: 'registrations', omniauth_callbacks: 'callbacks'}

after this update, the program can be login by github account.

2. use scope.
    * scope is considered as a Class methods, it is not an instance method. 
       I previous delclare it as an instance method, and I kept on getting the errors. After google it, I understood that scope should be an class method. and it can be used to get the right objects from the database.
    *for my rails project, I need to get all the items from a particular list. my scope is delcared as following:
      scope :get_list_items_of, ->(list) { where("list_id == ?", list.id)}
			and it can be called as a class method. 

