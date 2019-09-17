---
layout: post
title:      "Final Project - React, Redux, and Rail"
date:       2019-09-16 18:08:17 -0400
permalink:  final_project_-_react_redux_and_rail
---


## Final project
Time is flying, the couses are all finished, time for us to put all our knowledge what we learned from the past few months into the final project. It should be a fun journey!

## Project - 
This project is helping a small cafe (not as formal as restaurant) to track the food ingredients consummation.
### Database:
- ingredients: this is for tracking the major ingredients that used for making dishes       
     - name     
     - unit cost     
     - consumption
     - available amount    
     - alert low amount    

- dishes: this is the manu of the dishes this cafe provides        
     - name    
     - price  
     - ordered times    
 
- dish-ingredients : the major ingredients for each dish  
     - dish_id    
     - ingredient_id    
     - usage    
  
- orders: keep tracking the order of each table, and for the receipt  
     - table#    
     - total amount    
     - completed   

- order-dishes:    
    - order_id   
    - dish_id
		
		
		
 
### router:
- home
   -  display the tables  
   -  each table has  
       -  order button
       -  checkout button
       -  table available/unavailable  
   - kitech button  
      - will inform the kitech helpers to claim the needed ingredients to clean up  
   - inventory button  
      - will inform the mangers at least one ingredient is lower than the alerted low amount 
      
 
- kitchen  
   - list all the ingredients that need to be cleaned for making the ordered dishes  
   - list the ordered dishes for chefs to prepare  
 

- inventory
  - list the remaining ingredients in real time
  - if the ingredients are lower than alerted low amount, manager can submit the order form to restack the ingredients  
 
  
  


