---
author: Rachel Tomisin
date: 2021-11-24
title: Differences Between Browser Router and Hash Router
image: "router.png"
---

##

### **Introduction to Routing in React**

Routing is a very important aspect of every website. In react Js, routing is a process that allows a user to navigate to the different URLs that make up a react application. This is made possible through the use of a standard library system called React Router. With react-router, we can define multiple routes in our applications and render different components present in the app based on the route that matches the current URL being used. React router enables one to handle routing on the client-side of a web application, thereby mitigating the issue of the old way of serving pages from the server side where pages refresh on every visit (i.e. making unnecessary calls to the server-side).

To effectively understanding this article, you need to have a basic understanding of react and react routing
The react-router package consists of 3 different routers that we can make use of when building our apps. These routers include Browser Router, Hash Router, and Memory Router.
In this article, we will be focusing on the differences between Browser Router and Hash Router and why we should use them in our applications.

### **What is Browser Router?**

Browser Router acts as a parent component that stores all of the other components present in our applications. It uses the HTML5 history API (pushState, replaceState, and the popstate event) by manipulating the browser session history to ensure that our UI matches its current URL.
A browser session history keeps track of all the pages visited in a browser tab and also provides useful properties that enable one to navigate back and forth in the browser using the user's history. Browser router makes use of the web server and also needs to be configured in other to function properly. This configuration is what makes routing on the client-side possible, otherwise one would get a "404 not found" error when visiting a particular page rendered in a browser. This is because this route only exists on the client-side and not on our server, therefore, browser router needs to be backed by a web server for it to be able to send back the different pages for all the dynamic paths in our app.
Using the Browser router in our app, we will need to import it into our application like this.

```js
import { BrowserRouter as Router } from "react-router-dom";
```

The above line means we just renamed “BrowserRouter” to “Router”, that’s all it does;
And we can then wrap the router around our application.

```js
ReactDOM.render(
  <React.StrictMode>
    <Router>
      <App />
    </Router>
  </React.StrictMode>,
  document.getElementById("root")
);
```

It's only best to use browser router when building large applications that require a server, though, the react-router-dom team advises one to use the browser router always and also try to configure it to work on all our applications.

### **What is Hash Router?**

The Hash router on the other hand uses the client-side hash routing (i.e window.location.hash) to ensure that your UI matches its current URL in your browser. Whenever a new page gets rendered, the hash routes get appended to the browser URL, like this localhost:3000/#/about. The hash router usually does not require a web server to load a page because its hash URL ( e.g. localhost:3000/#/about ) cannot be read from the server, it's usually handled by react-router, which makes configuration easier. Using hash router in your app is not recommended by the react-router-dom team because it does not support legacy browsers and might also be considered bad for SEO because search engines only rank contents that are available on first load.
To use hash router in our app, we will also import the hash router

```js
import { HashRouter as Router } from "react-router-dom";
```

and use it in our app like this;

```js
ReactDOM.render(
  <React.StrictMode>
    <Router>
      <App />
    </Router>
  </React.StrictMode>,
  document.getElementById("root")
);
```

If you're trying to build static applications that only require one to use host providers like Netlify and SEO is not of utmost importance, then using hash router might be the best option.

### **Highlights of the Major Differences Between Browser Router and Hash Router**

| Browser Router                                                                                                                  | Hash Router                                                  |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Uses HTML5 history API                                                                                                          | Uses client-side hash routing i.e window.location.hash       |
| The URL does not have a hash(#) symbol appended to it, hence, makes the URL more readable and cleaner. E.g localhost:3000/login | A hash # is appended to the URL. E.g localhost: 3000/#/login |
| It supports legacy browsers.                                                                                                    | It does not support legacy browsers e.g IE9                  |
| It requires configuration in the browser to handle routes.                                                                      | It requires no server                                        |
|                                                                                                                                 |

### **Conclusion**

So far in this article, we have briefly described routing in ReactJs, we've explored the characteristics of both browser router and hash router, and have also understood their use cases. It is safe to say that both routers are good, but it is mostly advisable to use Browser router when building large applications that require one to have a hosting provider and also use Hash router when using host providers that only supports static applications (e.g Netlify).
