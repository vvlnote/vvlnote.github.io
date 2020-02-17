---
layout: post
title:      "Summary of setting up Express and MongoDB as Backend Server"
date:       2020-02-16 20:07:27 -0500
permalink:  summary_of_setting_up_express_and_mongodb_as_backend_server
---


## Install  Express.js and MongoDB as backend server
1. Create a folder with your project name.  
2. cd to the folder that you just created.  
3. Run npm init.  
    * For the backend, the start poinst is server.js  
    * License : "MIT"
    After above type in, you will get a package.json file under the folder.  
1.  Install dependencies:  
       npm i express body-parser mongoose concourrently cors dotenv
			 
    *  Express is a Node.js web application server framework, designed for building single-page, multi-page, and bybrid web application will be creating routers or APIs   
    *  body-parser is a middleware in order for application to be able to ready the body of an incoming JSON object.   If express.js version is 4.16+, the exrpess.js package included this middleware. so you do not need to to install this.  
    *  mongoose is an **ODM** (Object Data Modeling) library for MongoDB and Node.js.  
       It manages relationships between data, provides shcema validation, and is used to translated between objects in code and the represenation of those objects in MongoDB.  
    * concurrently, this can run multiple comaands concurrently.  After this is installed, you can set up your NPM start script (in package.json file) to run multiple commands by spearating each individual command with quotes.  	 
       You can reference this article to learn more [4 Solutions to Run Multiple Node.js or NPM commands Simultaneously](https://itnext.io/4-solutions-to-run-multiple-node-js-or-npm-commands-simultaneously-9edaa6215a93)  
    * cors stands for Cross-origin resource sharing, it allows AJAX requests to skip the Same-origin police and access resources from remote hosts. 
       The cors package provides an Express middleware that can enable CORS with different options.	  
    * detenv loads environment variables from a .env file into process.env. This makes developmenet simpler. Instead of setting environment variables on our app, they can be stored in a file, it is .env file. 		 

1.  npm i -D nodemon  
       nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in teh directory are detected.  
	  nodemon does not require any additional changes to your code. nodemon is a replacement wrapper for node, to use nodemon replace the word nonde on the command line when executing script.   
		-D will save nodemon as developmenet dependency, since we do not need it in production environment.  
		
    on terminal:
		
	`nodemon [your node app]`    

		 
### Update package.json to run the script.  
     open package.json file, and update the following:  

```
 "scripts": {
    "start" : "node server.js",
		"server": 'nodemon server.js"
  },   
```   

		 
node server.js => need to restart the server.js everytime you update the files.
nodemon server.js => it will automatcally rerun the server.js when you save your updates/changes.  

### How to kill tangling node process
Sometime, if you accidently closed the terminal without stop the node process, and if you try to run the same app, you won't be able to run, because this process is still running on the backgroud.
So the first thing to check is to find if this node processes are still running by typing:  
```
ps -ef | grep ndoe
# or
ps aux | grep node
```  

These commands will pring all the node process running.

Find the node process pointing to your script or server.js file and note down the process ID. then just kill it.   

```
kill -9 PROCESS_ID
# or
kill -1 PROCESS_ID
```  

-9 : This will stop the process dead in its tracks but it may leave any chile processes still running.  
-1: This tells the process to hangup just as you were logging out. The system will attemp to kill any child process associated with this process.  



## Run MongoDB remotely
I am using this online MongoDB, please click on [MongoDB](https://account.mongodb.com/account/login).  
If you do not have account with it, you can sign up, for testing purpose, it is free. Or you can use your own online MongoDB, or use the local mongoDB as well. In this summary, I will record what I did to set up the remote MongoDB.  

If this is first time to use this website. You will encounter the following page:

![Create New Clust](https://miro.medium.com/max/1760/0*cjCFm2P8baJwgzMZ)


I select the free program, and select the reginon. 

The 2nd step, you need to set up some info the is needed.  

![Connect to Cluster0](https://miro.medium.com/max/901/0*FTbUEi0MmEFQ8WyL)  

Click on Add Your Current IP Address to put your IP address which is used to connect MongoDB.  
You also need to create a MongoDB user, and the connection will contain this information in order to connect to MongoDB.   After you type in the user name, and password, you click on Create MongoDB User.  


The 3rd step you can select what method you would use to connect to MongoDB, in my case, I select Connect Your Application.  

![](https://miro.medium.com/max/1533/0*S3ICxNhoECtwePqg)

The 4th step will provide you a connection string that you need to put into your application to connect to MongoDB via your application.  

![](https://miro.medium.com/max/1529/0*N3_DR7tYkTvJN1jv)  

Click on Copy button to copy the connection string, and add it to your application code.  




