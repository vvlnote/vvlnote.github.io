---
layout: post
title:      "Sinatra Project : Property Management application"
date:       2019-05-16 21:28:51 -0400
permalink:  sinatra_project_property_management_application
---




This project will be implemented in Sinatra Web framework with MVC application
There are the following:
* Controllers

   *ApplicationController
	     - index.erb link to signup or login page
	    
	 *UserController
	     -get '/signup'
			 -post '/signup'
			 -get '/login'
			 -post '/login
			 -get'/logout
			 
	 *PropertyController
	     - get '/properties'
			 - get 'properties/new'
			 - post 'properties'
			 - get 'properties/:id/edit
			 - patch '/properties/:id
			 - get '/properties/:id
			 - delete '/properties/:id
			 
	 *WorkLogController
	     - get '/worklogs'
	     - get 'worklogs/new'
	     - post 'worklogs'
	     - get 'worklogs/:id/edit
	     - patch 'worklogs/:id'
	     - delete 'worklogs/:id'
	     
* Models
     *user: user_name, email, password, is_admin
		 *property: name, address, lease_starting_date, lease_ending_date, secuirty_deposit, rent, user_id
		 
		 user manages many properties
		 property is managed by a user
			
* Views
   - users:
          -  login => for the registered user to log in to this app
          -  new => sign up as new user
    - properties:
          - edit
          - index
          - new
          - show

## The steps to implement this project:


Learned from the mistake
1. session
     - if "session_secret" did not set or typo, the newly added keys in the session can not be access in the other routes
     - since the session is enabled, and session_secret is set, and the class User has macro : has_secure_password. when you save the user data without the password, this data record won't be able to be saved into the database
2. sinatra::flash
     - I try to display the error message via sinatra flash. I follow the steps that listed in https://github.com/SFEley/sinatra-flash. 
     - I did the following steps:
         a. install sinatra-flash
				 b. insert 'require sinatra/flash' in the application_controller.rb file (since all the controller classes are inherented from application_controller class, sinatra/flash will be seen in all the inhrented classes)
				 c. my application is inherented from Sinatra::Base, in order for sinatra/flash to work, I need to register Sinatra::Flash
		 - all the basic steps are completed
	
	When I ran shotgun, I have encountered an error: loaderror: cannot load such file -- sinatra/flash. 
	I have google it, no such error was encountered before. I found a post had loaderror with other file. And according to the messages, after update the Gemfile to include the specific gem that flaged the loaderror, then shotgun could run smoothly.
	I add "gem 'sinatra-flash' into the Gemfile, save it, and ran shotgun, it works as well. 
