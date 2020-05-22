---
layout: post
title:      "Axios or Fetch"
date:       2020-02-23 20:23:25 -0500
permalink:  axios_or_fetch
---


Axios is a Javascript library used to make http requests from node.js, and it supports the Promise API. Another feature that it has over .fetch() is that it performs automatic transoforms of JSON data.  


fetch() method defined on the window object, which you can use to perform requests. This method returns a Promise that you can use to retrieve the resposne of the request.  fetch() method is used instead of XMLHttpRequest, since it is a Promise-based.  


### Set up  
#### Axios
Before you can use Axios, you need to install it. 

```
npm i axios
```  

#### fetch() 
This is a built in function in the Node.js, so you do not need to install it separately.    



### Syntax  

**axios()**

The basic syntax for axios() is as following: 
```
const url = 'http://example.com/movies.json';
axios.get(url).then(response => console.log(response));
```

axios just retunrs the data object (response) in the JSON format, we do not need to use .json() to convert it.  

```
axios.get(url)
   .then(response => console.log(response))
	 .catch(error => console.log(error));
```

anxios will throw error with http request, and the .catch() block is executed.   
  
**fetch() **   

The basic syntax for fetch() is as following:  

```
fetch('http://example.com/movies.json')
  .then(response => response.json())
  .then(data => console.log(data));
```  

Note: .fetch() there is a two-step process when handling JSON data. The first step is to make the actual request and then the second is to call the .json() method ont he response.

There is something to be aware of about the error about fetch request. In .fetch() request, we will get 'error' only if network error isecountered while in all other cases if will return 'OK'.  


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

#### Difference between Axios and Fetch   

Fetch JSON post request:   
```
let url = 'https://someurl.com';
let options = {
            method: 'POST',
            mode: 'cors',
            headers: {
                'Accept': 'application/json',
                'Content-Type': 'application/json;charset=UTF-8'
            },
            body: JSON.stringify({
                property_one: value_one,
                property_two: value_two
            })
        };
let response = await fetch(url, options);
let responseOK = response && response.ok;
if (responseOK) {
    let data = await response.json();
    // do something with data
}
```   

Axios JSON post request:   

```
let url = 'https://someurl.com';
let options = {
            method: 'POST',
            url: url,
            headers: {
                'Accept': 'application/json',
                'Content-Type': 'application/json;charset=UTF-8'
            },
            data: {
                property_one: value_one,
                property_two: value_two
            }
        };
let response = await axios(options);
let responseOK = response && response.status === 200 && response.statusText === 'OK';
if (responseOK) {
    let data = await response.data;
    // do something with data
}
```  

From above examples, we can conclude the following differences:   
* Fetch is built into most modern browsers; no installation is required, Axios is a stand-alone 3rd party package that need to be installed before it can be used.  
* Fetch's body = Axios' data.  
* Fetch's body has to be stringified, Axios' data contains the object.  
* Fetch has no url in the request object, Axios has url in request object.  
* Fetch request function includes the url as parameter, Axios request function does not include the url as paramenter.   
* Fetch requset is OK when response object contains the ok property, Axiso request is ok when the response status is 200 and statusText is 'OK'.  
* Fetch is a two-step process when handling JSON data, first, to make the actual request; second, to call the .json() method on the response, Axios performs automatic transforms of JSON data.  
* Axios allows cancelling request and request timeout.    











