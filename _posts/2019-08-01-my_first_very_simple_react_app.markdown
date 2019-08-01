---
layout: post
title:      "My first very simple React app"
date:       2019-08-01 20:55:24 +0000
permalink:  my_first_very_simple_react_app
---

I am pretty exicted to learn about the React. This is a very popular framework in recently. The reason from what I understand, it could make the code more modulized, so the code can be easily to maintain and developed for the big project.

Since I just learned, and I would like to implement a very simple code, it contains state, props, and functional compoment. 

### Project
   While I follow the progress of the Curriculum, there is one lesson that need to implement callback function. In general, the curriculum would provide us some content relating to the lab, but this time, it seems use the different way, and also, we have done a lot of callback function in the JavaScript, so I guess the lesson would like us to figure it out by ourselves. 
	 
### setState() 
React Docs now recommends using function with prevState inside of setState
in the old fashion, if we like to update the state based on the current state value, then we save the current state value into a variable, then call setState() the update the state value by using the variable that carries the current state.

Now, the React recommend  using a function inside of setState that takes in prevState and an optional props parameter.
