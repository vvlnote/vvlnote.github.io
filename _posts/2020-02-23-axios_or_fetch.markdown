---
layout: post
title:      "Axios or Fetch"
date:       2020-02-24 01:23:24 +0000
permalink:  axios_or_fetch
---


Axios is a Javascript library used to make http requests from node.js, and it supports the Promise API. Another feature that it has over .fetch() is tha tis performs automatic transoforms of JSON data.  
If you use .fetch() there is a 2-step process when handing JSON data. The first is to make the actual request and then the second  is to call the .json() method on the response.  

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
