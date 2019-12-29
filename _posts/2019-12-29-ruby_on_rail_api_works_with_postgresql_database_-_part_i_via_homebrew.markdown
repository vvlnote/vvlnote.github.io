---
layout: post
title:      "Ruby on Rail API works with PostgreSQL Database - Part I via Homebrew"
date:       2019-12-29 18:30:55 +0000
permalink:  ruby_on_rail_api_works_with_postgresql_database_-_part_i_via_homebrew
---


The content of your blog post goes here.
My original Ruby on Rail backend app connecting to default database sqlite3, however, the app encountered concurrency issues, if I update several data records at about 3 seconds appart, the database would be locked up, and the app will suffer data lost, and cause the database in incorrect stage. 

So I would like to swich my database to PostgreSQL, it can handles concurrency data update better than sqlite3. 

Since I used brew to install PostgreSQL, I did not set up the password, and I am not able to setup the database that can works with my app. so I tried to reinsall it from [PostgreSQL download site](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).


### Install PostgreSQL via Homebrew on MacOS  
1. install PostgreSQL via Homebrew to get the latest version of PostgreSQL

    `brew install postgresql`  
		
2.  after the installation is completed, you can check with version of psotgresql you installed.  

    `postgres -V`  

    the version I installed is:  
		
		`postgres (PostgreSQL) 12.1`
		

3.  Add PostSQL binary in PATH variable in order to access the PostSQL command lien tools (i.e. psql).  

    `echo 'export PATH="/usr/local/opt/postgresql@12/bin:$PATH"' >> ~/.bash_profile`  
		`source ~/.bash_profile`    => apply the changes you made to ~/.bash_profile
		
    Note: @12 is the version I installed. so replace it with the version of PostgreSQL installed in your computer.  
		
4.  To start PostgreSQL service and enable to start to login.   

     `brew services start postgresql@12`  
		 
5.  We need to create a Database Role for the Rails application

     `createuser -P -d appname`  
		 
	   Note: 
    -	This is the place that I got stuck at first trial. When I created my Ruby on Rails app and connect to -database postgresql, and after all the migration files were created, and I tried to run rack db:migrate, the program complained that there is no connection to the PostgreSQL. and at that time I kept on trying and looking up internet to solve my issue, but I could not find the right method until I read  [How to Use PostgreSQL with Your Ruby on Rails Application on macOS](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-macos).   and this paragraph resolve my confusion:  I am confused by the password to access PostgreSQL service, and the password of the new role you created. 
            
>  In PostgreSQL, roles can be used to organize permissions and authorization. When starting PostgreSQL with Homebrew, you will automatically have a superuser role created with your macOS username. In order to keep these superuser privileges separate from the database instance you use for your Rails application, in this step you will create a new role with less access.


   -   appname is your application name, but you can select any name to become the username that you will put into  config/database.yml  in your Rails app.  
   -   '-d' to give this role the permission to create a database.  
   -   '-P' is to provide the password for this role, and this password needs to be put into the config/databse.yml
  

After you complete all the 5 steps, and you can generate your Ruby on Rail by "rails new appname -d=postgresql', and update config/databse.yml based on the username and password you entered when you run createuser command.  

Note: for the detail information , please refer to [How to Use PostgreSQL with Your Ruby on Rails Application on macOS](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-macos).












### Install PostgreSQL   - from downloading PostgreSQL from the web site

1.  If  PostgreSQL was installed by Homebrew, make sure that PostgreSQL was not running.   

    `brew services stop postgres `
    
   
2.  Uninstall PostgreSQL via Homebrew.    

    `brew uninstall postgresql`  
		
3.  Remove all local PostgreSQL files. 

     ```
     rm -rf rm -rf /usr/local/var/postgres  
     rm -rf .psql.local .psql_history .psqlrc.local l.psqlrc .pgpass
     ```  
		 
4.  Confirm PostgreSQL unistalled successfully.  
     `brew list postgres`  
		 
      if PostgreSQL uninstalled successfully, you should get the following error message:   
			`Error: No such keg: /usr/local/Cellar/postgresql`

5.  Go the [PostgreSQL download site](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) to download PostgresSQL.   

6.  Follow the wizard to install the PostgresSQL to your local system.   
    Note:  the defult  superuser name of PostgresSQL is postgres, and make sure to memorize the password. when you need to use superuser, you need to provide the password in order for you to login as superuser.

7. How to confirm PostgreSQL is installed successfully.  Please refer to the section "Verify the Installation" in [Install PostgreSQL](http://www.postgresqltutorial.com/install-postgresql/).

Note: I followed through all the steps that listed in [Install and setup PostgreSqL for Ruby on Rails on Mac OS](https://yizeng.me/2015/02/09/install-and-setup-postgresql-for-ruby-on-rails-on-mac-os/). I still keep on getting an error message for no database connection.  I need to have more time to figure out how to make it work. However, my first priority is to make my Ruby on Rails to work with PostgreSQL. So I use Homebrew to install PostgreSQL instead. Please refer to section: **Install PostgreSQL via Homebrew on MacOS **

I will try to get into this issue later on, and will update this post accordingly.






