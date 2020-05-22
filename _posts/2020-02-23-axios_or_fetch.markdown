---
layout: post
title:      "Axios or Fetch"
date:       2020-02-23 20:23:25 -0500
permalink:  axios_or_fetch
---


Axios is a Javascript library used to make http requests from node.js, and it supports the Promise API. Another feature that it has over .fetch() is that it performs automatic transoforms of JSON data.  


fetch() method defined on the window object, which you can use to perform requests. This method returns a Promise that you can use to retrieve the resposne of the request.  fetch() method is used instead of XMLHttpRequest, since it is a Promise-based.  
If you use .fetch() there is a 2-step process when handing JSON data. The first is to make the actual request and then the second  is to call the .json() method on the response.  

### Set up
#### Axios
Before you can use Axios, you need to install it. 

```
npm i axios
```  

#### fetch() 
This is a built in function in the Node.js, so you do not need to install it separately. 


### Syntax


How .fetch() hanldes error response. 


```
fetch('/api/auth/user', {
    method: 'GET',
    config
}).then(res => {
    console.log('res.status = ${res.status}');
    if (res.status >= 200 && res.status <= 299) {
        return res;
    } else {
        throw Error(res.statusText);
    }
}).then(res => {
    return res.json();
}).then(data => {
    dispatch({
        type: USER_LOADED,
        payload: data
})}).catch(err => {
    console.log(`err = ${err.message}`);
    dispatch(returnErrors(err.response.data, err.response.status))
    dispatch({
        type: AUTH_ERROR
    })
})
```  

There is something to be aware of about the error about fetch request. In fetch request, we will get 'error' only if network error isecountered while in all other cases if will return 'OK'.  

The basic syntax for fetch() is as following:  

```
fetch('http://example.com/movies.json')
  .then(response => response.json())
  .then(data => console.log(data));
```  

The returned response object contains the following properties:  
* Response.status
* Response.statusText
* Response.ok

From these properties, we can get more detail information about the status of response instead of  the OK flag.  So in order to handle the error from the response object, we can rewrite the above code as following:  

```
fetch('http://example.com/movies.json')
  .then(response =>{
	    if (response.ok) {
			    return response;
			}
			throw Error(response.statusText);
	}).then(response => response.json())
  .then(data => console.log(data))
	.catch(error => console.log(error););
```    





