[◀◀ Back](/README.md)

# Event-Driven Programming in Node.js 


- what is Event-Driven Programming in Node.js ? 

Event-Driven Programming is a logical pattern that we can choose to confine our programming within to avoid issues of complexity and collision. 

## Overview

- Every time you interact with a webpage through it’s user interface, an event is happening. 
- When you click a button a click event is triggered.
- When you press a key a keydown event is triggered.

 These events have associated functions that, when triggered, are executed to make a change to the user interface in some way.

## concepts of Event-Driven Programming :

- An Event Handler is a callback function that will be called when an event is triggered.

- A Main Loop listens for event triggers and calls the associated event handler for that event.


## EventEmitter

Node.js natively provides us with a useful module called `EventEmitter` that `allows` us to get started incorporating `Event-Driven Programming` in our project right away. Of course, creating our own version of EventEmitter wouldn’t be much of a challange, and in fact there are several modules published on `npm` such as `EventEmitter2` and `EventEmitter3` which promise a faster performance than the native EventEmitter.

- We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.

```js
const EventEmitter = require('events').EventEmitter;
const myEventEmitter = new EventEmitter;
```
Now we can get started with Event-Driven Programming in `Node`.

Imagine we’re creating a `chat room`. We want to alert everyone when a new user joins the chat room. We’ll need an event listener for a userJoined event. First, we’ll write a function that will act as our event listener, then we can use EventEmitters on method to set the listener.
 ```js
const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function userJoined(username){
  alertAllUsers('User ' + username + ' has joined the chat.');
}
chatRoomEvents.on('userJoined', userJoined);
```
The next step would be to make sure that our chat room triggers a userJoined event whenever someone logs in so that our event handler is called. 

```js
function login(username){
  chatRoomEvents.emit('userJoined', username);
}
```
We could expand further by creating events for when a user logs out, when a message is sent, when a message is received, or any other event we could possibly need for our chat room to be as dynamic as we want it.

## Removing Listeners
- (the event is no longer needed) or to avoid memory leaks 

- we can use the `removeListener` or `removeAllListeners` method. It’s important to note that in the `EventEmitter` that comes` built-in` with `Node` you must pass a reference to the exact function you wish to remove when using the removeListener method. 

```js

const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function userJoined(username){
  chatRoomEvents.on('message', function(message){
    document.write(message);
  })
}

chatRoomEvents.on('userJoined', userJoined);
All of that headache can be avoided if we rewrite the code like so:

const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function displayMessage(message){
  document.write(message);
}

function userJoined(username){
  chatRoomEvents.on('message', displayMessage);
}

chatRoomEvents.on('userJoined', userJoined);
Now if we want to remove the displayMessage function from the message event’s list of handlers:

chatRoomEvents.removeListener('message', displayMessage);
```
#  Object Oriented Programming + Event-Driven Programming

 - the combination of the `Object Oriented` and `Event-driven programming paradigms`. 

- The Object Oriented approach promotes the idea that all behavior of an individual unit (or object) be handled from code within that unit. Using this approach, applications are built with many different units that all speak to and interact with each other.

- building a` mail application`. We might have an `object` whose sole purpose is to process the incoming and outgoing mail messages for our client. This object would contain all of its own behavioral functions. We might have a sendMail function that delivers our mail to a server. We might also have a receiveMail function that tells the server to deliver us any new mail it has for us. We’ll call the object responsible for these server interactions our Mailbox.

```js
const Mailbox = {
  sendMail: function(){
    // code to send mail.
  },
  receiveMail: function(){
    // check server for new mail.
  }
}
```

- Now if we are building other units that want to make use of our sendMail function, they can access it through Mailbox.sendMail. This is a standard approach.

- we also want to log the mail every time we send it :

We now need to either modify our sendMail function to incorporate this behavior, or create another function that is triggered immediately after the sendMail function. In which case the object responsible for triggering the sendMail function must be sure to also trigger the log function. As our applications get more complex, and as new sequences of behavior are added, this could get somewhat out of hand.

- This is where we can make use of Event-driven programming. 

- ex : hungry alligator, represented by the gator class. Using a non-event-driven approach, the process of eating for our alligator looks like this:

```js
class Food {
  constructor(name) {
    this.name = name;
  }

  becomeEaten() {
    return 'I have been eaten.';
  }
}

var bacon = new Food('bacon');

class gator {
  eat() {
    bacon.becomeEaten();
  }
}
```

- In this example, our gator had to access the methods inside of Food in order to eat. This is a lot of work for our lazy gator so we’re going to make things easier for him.

```js
const EventEmitter = require('events').EventEmitter;
const myGatorEvents = new EventEmitter;

class Food {
  constructor(name) {
    this.name = name;
    // Become eaten when gator emits 'gatorEat'
    myGatorEvents.on('gatorEat', this.becomeEaten);
  }

  becomeEaten(){
    return 'I have been eaten.';
  }
}

var bacon = new Food('bacon');

const gator = {
  eat() {
    myGatorEvents.emit('gatorEat');
  }
}
```
Now all our gator has to do is just say gatorEat and the EventEmitter takes care of the rest


references : [digitalocean.com](https://www.digitalocean.com/community/tutorials/nodejs-event-driven-programming)