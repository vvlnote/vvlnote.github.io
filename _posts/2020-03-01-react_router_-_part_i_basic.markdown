---
layout: post
title:      "React Router - Part I (Basic)"
date:       2020-03-02 02:41:38 +0000
permalink:  react_router_-_part_i_basic
---


The reason I need to div into react route is because I need to route to the pages after user login/register, and all the pages after register/login only displayed the information relating to the logined users. So I need to have a router and find a way to job into the particulare starting pages  to handle this kind of scenario.

### How react loads pages
/src/index.js  is the first file to be loaded, the initialization point of everything in the App. 

### React Router Set Up

React.js is a very slim library, if you need to implement router in your project, you need to install it explicitly.  
The react router contains 3 main packages, they are :  
* react-router : This package provides the core routing functionality for React Router, however, you  won't install it directly.  When you install one of the following packages, react-router is alreayd included.  
* react-router-dom: It contains the DOM bindings for React Router, and this router package is for websites router implemenation.  
* react-router-native: It contains the React Native bindings for React Router.. The router components are for React Navtie development environment.  

Since the application I am working on is a web app,  I install  **react-router-dom**.  Then you need to import it whenever you need to have routers.  

In general, the following APIs need to be imported:  

```
import { BrowserRouter as Router,  Route,  Link, Redirect, NavLink  } from 'react-router-dom';
```  



### React Router Primary Components  
There are 3 primary components are included in **react-router-dom**,  they are:  
* **Routers**, like BrowserRouter and HashRouter. I use BrowserRouter in my web app. For detail between BrowserRouter and HashRouter please refer to [Router](https://reacttraining.com/react-router/web/guides/primary-components)  
* **Route Matcher**, like Route and Switch.  
* **Navigation** (or route changer), like Link, NavLink, and Redirect.  

##### Router  :
* For my app, I use **BrowserRouter**. The differences  between BrowserRouter and HashRouter please refer to [Router](https://reacttraining.com/react-router/web/guides/primary-components)  
* To use a router, make user it is renedered at the root of your element hierarachy. Typically you'll wrap your tope-level App element in a router.  Either in the src/index.js or in the src/App.js.

```
ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  document.getElementById("root")
```   

* It is important to mention that a router component can only have one child element, otherwise it would throw error message.  
* **The main job of a Router component is to create a history object to keep track of the location (URL). **

##### Router Matcher  
**Switch**  
* It works like switch in the Javascript. It will search through all the elements (they are Route elements) inside the Switch Component to find one Route element whoes path matches the current URL, and all the Route elements after the matched path would be ignored.   
For example, if you are looking for "/login" route, however, the first Route element inside the Switch component is "/", then "/" will be renendered instead of "/login".  The reason is:  
A Route path matches the beginning of the URL, not the whole path string. So Route path="/" will always match the URL.  
How can this confusion can be prevented?  There are 2 ways to prevent it:  
    1. Put Route path with more specific (typically longer) paths before less-specific paths.  
```
<Switch>
    <Route path='/login' componenet={loginPage} />
		<Route path='/' componenet={homePage} />
</Switch>
```  
    In the previous example, since path='/login' will be visited first, so the loginPage will be rendered correctly.

    1.  
```
<Switch>
    <Route **exact** path='/' componenet={homePage} />
		<Route path='/login component={loginPage} />
</Switch>
```  
    keyword: **exct** it would force to match the entire URL.  
		
**Route**  
It is used to rendered UI when its path matches the current URL.  
The following methonds are used to renender UI when the current URL match with Route path:  You should only one of these methodes on a given Route.
* Route Component  
* Route render  
* Route Children function  

All the above render methods will be passed the same route props as following:  
* **match**  
* **location**
* **history**  

##### Navigation (or Route Changers)  
* Link : create links in your application. Whenever you render a Link, and anchor a tag will be rendered in HTML document.  
* NavLink: this is a special type of Link, it can style itself as 'active' when its prop matches the current location.  
* Redirect : it can force navigation to the specific location.




### NavBar Component
NavBar component is omnipresent. It will be on all the pages. And it allow the user to navigate the website and to show the sections (routes) avaliable. 



Reference:   
[React Router DOM: Setup, essential components, and parameterized routes](https://blog.logrocket.com/react-router-dom-set-up-essential-components-parameterized-routes-505dc93642f1/)  
[Quick Start](https://reacttraining.com/react-router/web/guides/quick-start) 


