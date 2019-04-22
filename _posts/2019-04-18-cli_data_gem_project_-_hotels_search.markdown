---
layout: post
title:      "CLI Data Gem Project - Hotels search"
date:       2019-04-18 18:42:11 -0400
permalink:  cli_data_gem_project_-_hotels_search
---

Nowaday, traveling is a type of life style. We are all working so hard in our jobs, and lives. Right now, most of the companies emphasize on work and live banalace. Taking time out of office is a good way to refresh your minds, and gain more energy after you back from the vacation.

Planning trip route, finding suitable  hotels during the trip is a very time commsuing, but it will pay off if you can have a good rest during the trip and it will make your trip more pleasent and appreciated.

I decide to create a CLI Gem project that would scrape hotels.com to give the users a brief description of the hotels in the city they plan to visit so they can decide to look into more detail without scroll up and down of the web page. 

In this project, there are 3 classes, they are CLI, Scrape, and Hotel.

CLI class is for displaying the Commend line interface to have users  input the selections for displaying the requested information.

Scrape class is to get the handler of web page, so the program can use the APIs to retrieve the information from web pages.

Hotel class is to store the information relating to the hotel, and available rooms. 
The detail is as following: 
* name => hotel name
* address => hotel address
* attractions => listing all the closeby attractions which are provided by the web page, so user have a reference point
* guest review rate => display the rating based on the comments from the people who stayed in the hotel before
* price => the cheapest price for the hotel
* all => an array to contain all the hotels
* rooms => an array contains all the available rooms of the hote. Each room is stored as a hash object. (since in this projct, I only need  the properties of each room, there is no any required methods).

This is my first time to use the local machine to run the ruby/project, so I need to the followings before I start coding.
1. set up the envionment for running this project
2. need to have Git intialize
3. how to run the CLI project

I follow AVI's youtube, CLI Gem Walkthrough, to start setting up my local environment. I have encountered a lot of issues when I tried to install the needed ruby gems in order to run the projects The good thing is when I encouter issues, the log file give me a lot of information to resolve the issues. I am barely able to run the project. (I still have an issue for not able to run pry in my project. and still try to resolve this issue.)

After the enviroment is OK for running the project, I use the top-down method to proceed my project.
* What is the information this project should provide?
* What are the steps to go through this project?
* What kind of information this project needs in order to proceed?


The purpose of this project is helping us to be familiar with scraping the web page, so I only list 3 cities for practicing and the url of these 3 cities are semi-hard-coded. In order for a valid url, the users need to provide the check-in and check-out date to complete this url.

the followings are the process of this project:
1. users type in check-in/check-out date
2. behind the scenses, load the hotels information from the web page
3. based on the url of each hotel from item 2 to retreive the information of rooms
4. list the queries on terminal for user to choose 
5. base on the input from the terminal to list the needed information

What I learn from this project:
1. since I will be the full stack engineer, web development will be part of job description. so the consistent naming is very important. If the web page does not have consistent naming for the class or id, the scraping will be very difficult thing to do.


What can be improved/extended for this project:
* need to verify if the input check-in/check-out date
* allow user to type in the places instead of hard-coded place name
* can be combined with the Google maps to calculate the distance between the place you are going to visit and the hotel.
* need to resolve the issue about pry not working on my local environment

[https://www.youtube.com/watch?v=sg6xhkPUUik]

