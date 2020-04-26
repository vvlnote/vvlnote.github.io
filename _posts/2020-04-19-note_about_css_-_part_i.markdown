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

**CSS can be used for: **    
* Styling  
* Layout  
* Animations  
* Font Changes  
* Organization  
* Grid system  

**How is CSS used?**
* In general, a file is aved in a .css format, and use link tag in HTML to link the .css file to HTML page.  
* CSS selectors can be used to address some portion of HTML page to style and use.  
* HTML element class or id attributes are used to manipulate in CSS.
* Typicall, it follows this method: Select, then edit.  


CSS can be added to HTML elements in 3 ways:  
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
		
### CSS Selectors
CSS selectors are used to "find" the HTML elements that you want to style.  

CSS Selectors can be defined into 5 categories:  
* Simple Selectors : select elements based on tag name, class, and id.  
   * Element Selectors:  this is the most basic selectors.  
      ex:
			          p {
			                  color: blue;
												font-weight: bold;
									}  
      *  This applies to all of the elements with that tag on the page.  
      *  	It ranks (Specificity) on the bottom of the specificity scale. (its specificity score is 10).  		     
   * Class Selectors:  the class name of elements (tags) are the target.  
      ex:  
			       .title {
						       color: red;
									 text-align: left;
									 }  
     * This is used to select elements with a certain class name.
     * Can be used on any and all elements with this class name.  
     
   * ID Selectors: 
      ex:  
           #service-image {
					        background: url("servicelogo.png');
									}  
     * This is used to select elements with a certain ID name.  
     * Can be used on any and all elements with this ID name.  
     									
  * Universal Selector: *, selects all HTML elements on the page.  
     ex:  
		 * {
		          text-align: center;
							color: yellow;
				}
* Combinaton selectors:  
* Pseudo-class selectors:  
* Pseudo-element selectors:  
* Attribute Selectors:  

