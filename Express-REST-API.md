[main README](./README.md)

# Review to ES6 Classes :
what is classes : Classes are a template for creating objects,
Classes are in fact "special functions".  

how we use class in our code ? 
- we need to define it by :
- using a class declaration,we can declarate class by using the class keyword with the name of the class

example : 

```js
class car {
  constructor(Type, color , price) {
    this.Type = Type;
    this.color = color;
    this.price = price;
  }
}

```
-  another way to define a class is A class expression , Class expressions can be named or unnamed. 
The name given to a named class expression is local to the class's body.
- it can be accessed via the name property.


### ***hoisting in classes :*** 
is different from functions hoisting 
in functions we can call it any where any time ,
but when using classes you have to declarate if berfor calling it .

### Class body and method definitions :
 
-Strict mode
-Constructor
-Static initialization blocks
-Prototype methods
-Generator methods
-Static methods and properties 

## Express Routing :
Routing refers to how an application endpoint (URI) respond to client requests

Example:
app.get('/', (req, res) => {
  res.send('welcome')
})

in this example : a get request send to by client to the server on path "/" which is the home page 
and the client will recive a respones massage "welcome" 

and we have dirrerent type of ***request*** we can send it to the sever , like : 
-GET
-POST
-DELETE
-PUT
and each and every one of these methods we serponse on deferent way from the other :

GET request will Get data
delete request will delete data
post request will insert data
put request will update data

and we have dirrerent type of ***response*** we can send it to the client , like :

-res.download():	Prompt a file to be downloaded.
-res.end():	End the response process.
-res.json():	Send a JSON response.
-res.jsonp():	Send a JSON response with JSONP support.
-res.redirect()	:Redirect a request.
-res.render():	Render a view template.
-res.send()	:Send a response of various types.
-res.sendFile():	Send a file as an octet stream.
-res.sendStatus():	Set the response status code and send its string representation as the response body.


## express.Router: 

Use the express.Router class to create modular, mountable route handlers. A Router instance is a complete middleware and routing system; for this reason, it is often referred to as a “mini-app”.

 and we can : 
-Use express.Router() multiple times to define groups of routes
-Apply the express.Router() to a section of our site using app.use()
-Use route middleware to process requests
-Use route middleware to validate parameters using .param()
-Use app.route() as a shortcut to the Router to define multiple requests on a route

example :
```js
const express = require('express')
const router = express.Router()

// middleware that is specific to this router
router.use((req, res, next) => {
  console.log('Time: ', Date.now())
  next()
})
// define the home page route
router.get('/', (req, res) => {
  res.send('Birds home page')
})
// define the about route
router.get('/about', (req, res) => {
  res.send('About birds')
})

module.exports = router
Then, load the router module in the app:

const birds = require('./birds')

// ...

app.use('/birds', birds)
```
The app will now be able to handle requests to /birds and /birds/about, as well as call the timeLog middleware function that is specific to the route.

#### chained route 
app.route()
You can create chainable route handlers for a route path by using app.route().

 example of chained route handlers app.route().
```js
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book')
  })
  .post((req, res) => {
    res.send('Add a book')
  })
  .put((req, res) => {
    res.send('Update the book')
  })
  ```


