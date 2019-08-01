---
layout: post
title:      "Rails with JavaScript project"
date:       2019-08-01 17:30:24 +0000
permalink:  rails_with_javascript_project
---

This assignment, I was asked  to modify my previous Rails project, add dynamic features that are only through JavaScript and JSON APIs. And the JSON data is getting from the rails controller and appending the data from JSON to the DOM.

In the Rails application, controller taking care of the APIs, model taking care of accessing the database and returning the data in the format that is set in your model. View will display the data by using params. 

However, for this project, how can I achieve thees requirement using the existing Rails structure. 

After I review the following videoes:
https://www.youtube.com/watch?v=oHPM0ekV7zQ
https://www.youtube.com/watch?v=Yd0nH9CWWfo&amp=&feature=youtu.be

I have gotten a better understaining about this project structure:
* the routes that laid out from Rails project is where the URL that you passed into fetch() or AJSX.get() get the JSON data. 
* The files you implemented under controller of  the Rails project, need to set up to allow request to get the data in JSON format
* You are not using JavaScript to fetch / .get () to access database directly, you pass in the URL that listed in the routes, and when the controller receive the request,  the code you implemented in the controller will get the data via model, and return back to fetch()/.get().
* the same as create a new record.  

what I learned: 

* The main difference between the datalist and Select elements is the ability to enter a value not included in the option list. The datalist allows the user to enter any value, assuming it meets validation criteria, and the select element restricts values to those in the option list.
