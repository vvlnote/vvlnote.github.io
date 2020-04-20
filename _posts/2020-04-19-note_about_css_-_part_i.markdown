---
layout: post
title:      "Note about CSS - part I"
date:       2020-04-19 23:42:02 -0400
permalink:  note_about_css_-_part_i
---


I would like to refresh my CSS knowledge. This is my summary I can use as reference later on. 

### What is CSS?  

* CSS stands for Cascading Style Sheet.
* It is a language for designing or styling the web pages. 
* It is the standard for styling web sites, and used by most (or almost all) website across the web develpoment.  

**CSS can be used for:  **  
* Styling  
* Layout  
* Animations  
* Font Changes  
* Organization  
* Grid system  

**CSS can be added to HTML elements in 3 ways:  **  
* Inline  
   Use the style attribute in HTML elemets.  
	` i.e. <h1 style="color: red">Title</h1>`  
	 
* Internal  
  It is defined inside style element, inside the head section.  
	`<head>
	        <style>
					     body {
							     background: url("./background.png");
									 }
						</style>
	</head>`   
	
* External  
   It is defined within the link element, inside the head sction of an HTML page.  
	 
	 Example:   
	 `<html>
	     <head>
	        <link rel="stylesheet"  type="text/css"  href="../css/style.css">
			 </head>
		<html>`   
		
		

![](https://developer.mozilla.org/files/3537/linear-gradient.png)
