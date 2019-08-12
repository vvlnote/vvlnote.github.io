---
layout: post
title:      "Rails with JavaScript project"
date:       2019-08-01 13:30:24 -0400
permalink:  rails_with_javascript_project
---

This assignment, I was asked  to modify my previous Rails project, add dynamic features that are only through JavaScript and JSON APIs. And the JSON data is getting from the rails controller and appending the data from JSON to the DOM.

In the Rails application, controller taking care of the APIs, model taking care of accessing the database and returning the data in the format that is set in your model. View will display the data by using params. 

However, for this project, how can I achieve thees requirement using the existing Rails structure. 

After I review the following videoes:

[get data from Rails application]((http://)https://www.youtube.com/watch?v=oHPM0ekV7zQ)

[post data to reails model, and get the new data back]((http://)https://www.youtube.com/watch?v=Yd0nH9CWWfo&amp=&feature=youtu.be)

I have gotten a better understaining about this project structure:
* the routes that laid out from Rails project is where the URL that you passed into fetch() or AJSX.get() get the JSON data. 
* The files you implemented under controller of  the Rails project, need to set up to allow request to get the data in JSON format
* You are not using JavaScript to fetch / .get () to access database directly, you pass in the URL that listed in the routes, and when the controller receive the request,  the code you implemented in the controller will get the data via model, and return back to fetch()/.get().
* The same as create a new record.  

Advace: (not in the requirement)
* Add the new list items into the list
* Cross out the completed items
* Delete the not needed items

what I learned: 

* Duplicate the respository
   This assignment is based on the previous Rails project, and  extend to  JavaScript and JSON API. So the first thing is I need to duplicate the Rails project respositor to a new respository. So I can keep Rails project respository untauched.
	 First, I tried to fork the rails project, however, since this project is resident in my account, so the fork is not working this way.
	 There is a way to mirroring (duplicating) a respository. and the followings are the steps:
1. 	 In terminal, create a bared clode of the respository:  
       ex:  in terminal type  
			 `<git clone --bare https://github.com/exampleuser/old-repository.git>`
2. 	 Mirror-push to the new respository  
       ex:  
			 `<cd old-repository.git>`
       `<git push --mirror https://github.com/exampleuser/new-repository.git>`
3. 	 Remove the temporary local respository you created in step 1  
       ex:  
			 `<cd ..>`
       `<rm -rf old-repository.git>`
4. 	 You can start to work on your new respository.  
       In your new respository, all the logs from the old repository will be copied into this new repository


* The main difference between the datalist and Select elements is the ability to enter a value not included in the option list. The datalist allows the user to enter any value, assuming it meets validation criteria, and the select element restricts values to those in the option list.
* Disable forgery protection on controller.
   I did not use the form_for to generate my submit form, so when I try to do fetch with method: post, I always got the following error:  
	 422 (Unprocessable Entity).
	 By looking at the explaination from the  internet, it seems that the server understands the content type of the request eneity, and by looking at the terminal where rails server is running, I have seen another error:   
	 ActionController::InvalidAuthenticityToken (ActionController::InvalidAuthenticityToken):
	 
	 I thought it is due to that I did not pass in the authentication code like if I did form_for. for the short term solution, I tried to disable the forgery protection on the application_controller.  be aware, this is not a good practice to write the code, since it would expose your data in the internet, and everyone can access it, manipulate it. 
	 for now, I put the following code in the application_controller.rb
	 skip_before_action :verify_authenticity_token, this will skip the checking.
