---
layout: post
title:      "Set up pgAdmin 4 to connect PostgreSQL server, and view data via pgAdmin 4"
date:       2020-01-06 01:48:54 +0000
permalink:  set_up_pgadmin_4_to_connect_postgresql_server_and_view_data_via_pgadmin_4
---


In my previous post [Ruby on Rail API works with PostgreSQL Database - Part I via Homebrew](https://vvlnote.github.io/ruby_on_rail_api_works_with_postgresql_database_-_part_i_via_homebrew), I am able to view the data in PostgreSQL via CLI.  In this post, I would like to explore the data via GUI.  

By default, PostgreSQL installation comes with pgAdmin 4, if you download PostgreSQL from [PostgreSQL Database Download](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads), pgAdmin 4 is part of the download package. However, since I installed  PostgreSQL via Homebrew, pgAdim 4 needs to be installed separately later on. 

#### Befor install pgAdmin 4, the following tasks need to be completed :  

1.  Start or ensure  postgresql server is running:  

	  `brew services start postgresql`       or   

	  `ps auxwww | grep postgres`  
		
2.  Since PostgreSQL was installed  and started PostgreSQL server, you do not need to use native terminal on your Mac.  and create a superuser postgres  in order to log in pgAdmin.   Use the follow command to create.

  `createuser -s postgres`  
	
3.  After this user is created, you need to assign a password to this user, so later on, you can use this password to log in pgAdmin 4.

  `ALTER USER postgres WITH PASSWORD 'password';`  
	
	Note:
     * 	replace 'password' with the password that you like to assign to superuser postgres.
     * 	do not forget to put ; at the end of the command.   

#### Install pgAdmin 4  

   Download pgAdmin 4 application from [pgAdmin download page](https://www.pgadmin.org/download/).       
	 
Steps:   
   1.   Click on MacOS,  it will lead you to [pgAdmin 4 (macOS)](https://www.pgadmin.org/download/pgadmin-4-macos/), and select which version you like to download. And click on .dmg file to download.  
   2.   Click on the .dmg file on the download folder on Mac to opne up the application and install it. 
   3.   A window will pop up with the **pgAdmin 4** icon, and drap this icon into **application folder**.  pgAdmin 4 will be installed under application folder.  

 
#### Run pgAdmin 4  

*    Ensure the PostgreSQL server is running.  
*    Go to Application folder, click on pgAdmin 4 icon.  
*    A small pgAdmin window pops up to indicate Starting pgAdmin4 server...  
*    pgAdmin 4 will launch a webpage.  
*    It will ask you to type in the master password.   
     From what I learn, since PostgreSQL server was started by brew, so the master password is the same as the password you log in to your Mac. (if you find something different, please let me know.)  
* 	Then click on the PostgreSQL 12 ( this is the version installed on my Mac), it will pops up a a dialog to ask the password for 'postgres'. Type in the one you created on `ALTER USER postgres WITH PASSWORD 'password';`  
* 	After successfully log into the pgAdmin4, all the database you created will be displayed. 
		 
		 




	   







