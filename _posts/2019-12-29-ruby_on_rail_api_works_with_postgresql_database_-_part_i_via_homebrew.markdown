---
layout: post
title:      "Ruby on Rail API works with PostgreSQL Database - Part I via Homebrew"
date:       2019-12-29 13:30:56 -0500
permalink:  ruby_on_rail_api_works_with_postgresql_database_-_part_i_via_homebrew
---


My original Ruby on Rail backend app connecting to default database sqlite3, however, the app encountered concurrency issues, if I update several data records at about 3 seconds appart, the database would be locked up, and the app will suffer data lost, and cause the database in incorrect stage. 

So I would like to swich my database to PostgreSQL, it can handles concurrency data update better than sqlite3. 

Since I used brew to install PostgreSQL, I did not set up the password, and I am not able to setup the database that can works with my app. so I tried to reinsall it from [PostgreSQL download site](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).  However, I was not able to succeed to to link PostgreSQL to Ruby on Rails app. So for this post, I still used brew to install it.  

I will go back to install from PostgresSQL from the download site and try to link it with Ruby on Rails app  later on.  


### Install PostgreSQL via Homebrew on MacOS  

1. Install PostgreSQL via Homebrew to get the latest version of PostgreSQL

    `brew install postgresql`  
		
2. After the installation is completed, you can check with version of psotgresql you installed.  

    `postgres -V`  

    the version I installed is:  
		
		`postgres (PostgreSQL) 12.1`
		

3. Add PostSQL binary in PATH variable in order to access the PostSQL command lien tools (i.e. psql).  

    `echo 'export PATH="/usr/local/opt/postgresql@12/bin:$PATH"' >> ~/.bash_profile`  
		`source ~/.bash_profile`    => apply the changes you made to ~/.bash_profile
		
    Note: @12 is the version I installed. so replace it with the version of PostgreSQL installed in your computer.  
		
4. To start PostgreSQL service and enable to start to login.   

     `brew services start postgresql@12`  
		 
5. We need to create a Database Role for the Rails application

     `createuser -P -d appname`  
		 
		 
	  Note: 
    -	This is the place that I got stuck at first trial. When I created my Ruby on Rails app and connect to -database postgresql, and after all the migration files were created, and I tried to run rack db:migrate, the program complained that there is no connection to the PostgreSQL. and at that time I kept on trying and looking up internet to solve my issue, but I could not find the right method until I read  [How to Use PostgreSQL with Your Ruby on Rails Application on macOS](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-macos).   and this paragraph resolve my confusion:  I am confused by the password to access PostgreSQL service, and the password of the new role you created. 
            
>  In PostgreSQL, roles can be used to organize permissions and authorization. When starting PostgreSQL with Homebrew, you will automatically have a superuser role created with your macOS username. In order to keep these superuser privileges separate from the database instance you use for your Rails application, in this step you will create a new role with less access.


   -   appname is your application name, but you can select any name to become the username that you will put into  config/database.yml  in your Rails app.  
   -   '-d' to give this role the permission to create a database.  
   -   '-P' is to provide the password for this role, and this password needs to be put into the config/databse.yml
  

After you complete all the 5 steps, and you can generate your Ruby on Rail by "rails new appname -d=postgresql', and update config/databse.yml based on the username and password you entered when you run createuser command.  

Note: for the detail information , please refer to [How to Use PostgreSQL with Your Ruby on Rails Application on macOS](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-macos).


### View data in the database that created by Ruby on Rails app

- After you  update the config/database.yml with your database name, the user that can access this database, and the password to login to this database.  You can run the following commend to create the database that associates with newly created Rails app.

   `rails db:create`  
	 
	 The database that you specified in the config/database.yml will be created after this commend.  
	 
- After you set up all the migration files under Rails app, then run the  following commend wil generate the database schema.rb under db/schema.rb.  

  `rake db:migrate`  
	
-  If you create the sample data that stored under db/seeds.rb, run the follwoing commend to push the sample data into the database.

   `rake db:seed`  
	 
	 
- View the data in the database via CLI.  
    1.  Connect to the database:  
         ` psql databasename username`  
				 
    2.  Your terminal should show as `databasename => `.  
          This means that you are in the psql environment.    
					
         -  Show all the database:  

		         `\list`  
					 
         -  View the tables in your database:  

              `\dt`  
				 
         - 	View a particulare table:   
	
	            `\d tablename`  
				 
              the table name should match with the name that listed by \dt
				 
         -  View the data inside a particular table:  
             *  `TABLE tablename;`  
             *   `SELECT * FROM ingredients;`  

            Note: do not forget ";" at the end of the command.
				
         
				 
       	   
				 
	 
	
	
				 
				 
		
		
		





















