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
     - available_amount    
     - low_amount_alert .     

- dishes: this is the manu of the dishes this cafe provides        
     - name    
     - price  
     - total_orders     
 
- dish_ingredients : the major ingredients for each dish  
     - dish_id    
     - ingredient_id    
     - usage    

### state that kept inside the redux store, those data is not stored in the DB. 
- orders: keep tracking the order of each table, and for the receipt  
     - table#    
     - dishName
     - price   

 
### router:
- home
   -  display the tables  
   -  each table has  
       -  order button
       -  checkout button
       -  table available/unavailable  
   - inventory button  
      - will inform the mangers at least one ingredient is lower than the alerted low amount 

 

- inventory
  - a table to display the current inventory of ingredients
  - if the ingredients are lower than alerted low amount, manager can submit the order form to restack the ingredients  
 
  
## How this project works
- need to start rails server under the joy-cafe-sqlite-api to start the backend and database  
- run npm start under joy-cafe-client to bring up the front end app.  
- type in localhost:3000 in the browser to launch the app  
- in the first page, you can click on the order to lauch orders/tableId to select the dishes that you like to order, and click 'Place order" to save this order into the store state, and update the dishes total orders, and ingredient usage via rails server to the database    
- click on the Home button, the orders will be display on the page. you can either click on the pay to remove the order from the store orders.  
- click on the Inventory button to display the remaining ingredients as a table. you can click on the "order" button to submit an order form to add the ingredient to the database.
	
