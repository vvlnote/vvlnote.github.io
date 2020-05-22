---
layout: post
title:      "React Router - Part II "
date:       2020-03-08 21:23:46 -0400
permalink:  react_router_-_part_ii
---


There are several ways to redirect to other page in programmatic way.

* Link  
   the route is wrapped inside Link component. so when the link is clicked, the path/page inside the Link component would be loaded.  
* Redirect Component  
  We can redirect using Redirect component by siply passing the route we want to redirect to and rendering the component. 
	The easiest way to use this method is by maintaining a redirect property inside the state of the compoment.  
```
state = { redirect: null };
render() {
  if (this.state.redirect) {
    return <Redirect to={this.state.redirect} />
  }
  return(
  // Your Code goes here
  )
}
```  
   Whenever we want to redirect to another path, we can simply change the state to re-render the component, thus rendering the Recirect componet.  
	 
```
this.setState({ redirect: "/someRoute" });
```
* useHistory Hook  

```
import { useHistory } from "react-router-dom";

function App() {
  let history = useHistory();
}
```   
After this, we can use .push() method to redirect to any route we want.  
`history.push('/someRoute');`  

From above implementation, every component that is an immediate child of the Route compoment receives history object as a porp. 

* History prop  
  This is the same history (library) which keeps history of the session of React Router. We can thus use its properties to navigate to the required paths.  
```
this.props.history.push("/first");
```   
   There is a common problem that wwe can encounter is that in components which are not immediate child to teh Route compoment, there is no history prop present. This can be olved using the withRouter function. 

   withRouter is a function provided in the react-router-dom library that helps us access the history prop in components which are not immediate children to teh Route components.  
```
import { withRouter } from "react-router-dom";
```  
To get the history prop inside our component, we need to wrap our component with withRouter while exporting it. 
```
export default withRouter(yourComponent);  
```  

We can now access the history prop. 

* createHistory  
  Every time we need to redirect from, say example a redux action, we always have to pass history to the action, unnecessarily increasing the number of arguments. This method can be used to get a neater code.
	
	In this method, we make our custom history instance which we can import in other files to redirect. 
```
import createHistory from "history/createBrowserHistory";
export default createHistory();
```   

  As BrowserRouter uses its own history and does not accept any outer history property, we have to use Router instead of BrowserRouter.  

```
import { Router } from "react-router-dom";
import history from "./utils/history";

function App(){
  return(
    <Router history={history}>
    // Your Routes go here
    <Router>
  )
}
```  

After this, we can import this history instance in whichever file we want to redirect from.   

```
import history from "./utils/history";

history.push("/somePath");
```  


