# WE 3

## MEAN stack
* a stack often refers to the collection of technologies used in a given system
* the mean stack:
  1. M: MongoDB
  2. E: Express
  3. A: Angular
  4. Node.js

## backend / frontend
* backend: web servers like Node.js
* frontend: HTML / CSS / JS and all associated considerations on the client side (or in the browser)

## layers of the full-stack
1. server, network and hosting environment
2. data modeling
3. business logic
4. API layer/ Action layer/ MVC
5. UI
6. UX
7. understanding what the business/client need

## EVENT DRIVEN ARCHITECTURE
* EDA for short
* basically: when X happens, do Y
  * X = the event
  * Y = event handler
  * X can be a click event and Y can be turning a lightbulb
* this pattern lends itself well to async programming languages
* for the server side you can think of events that are handled by node.js like request/response

## DOM
* the DOM interface treats HTML as a tree structure where each node is an object that represents a part of the document
![DOM tree](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/DOM-model.svg/800px-DOM-model.svg.png)
* 1 reason why the browser turns HTML into the DOM is so that JS code can manipualte the webpage and respond to suer interactions liek clicking a button

## JQuery
* jquery is a library to handle client side events
* fixes browser compatiability issues
* cleaner API for ex:
  * `${"#foo"}` vs. `getElementById("foo")`

## Bubbling and Capturing
* since DOM elements are nested into other elements; events that affect a child bubble up through its parent
* to stop the bubbling type: `stopPropagation()`
* bubbling events stop once they reach the document object of the DOM
* `event.target` is the actual element beign clicked (this will never change during the whole bubbling phase)
* `this` or `event.currentTarget` is the current element. The one that has a currently running handler on it
* bubbling event goes from the target element staright up
* `event.stopPropagation()` stops moving upwards but on the current element all handlers still run
* `event.stopImmediatePropagation()` stops the bubbling and rpevents any handlers from running on the current element
* nested menu items is an example where you want to stop the bubblign process so that not all items get triggered/fired when just one si clicked.
  * but this will create a dead zone if you stop the bubblign for analytic software that calcualted mouse clicks
* [capturing diagram](https://javascript.info/bubbling-and-capturing#capturing)
* by default event handlers have the capturing phase set to false. to turn it on type `element.addeventListener(..., {capture: true})`
  * default is false which means the handler is set on the bubbling phase
  * `true` means the handler is set ont he capturing phase
* click [here](https://javascript.info/bubbling-and-capturing#summary) for a bubbling and capturing summary of key points

## click events
* setting a click events for each cell of a table of 1000 cells would eb anightmare and a memory hog. So using bubbling to our advantage we can set 1 click event on the table itself and then delegate any click events of its children elements

## AJAX
* by default when clicking a form button will submit a form to the form's actiona ttribute but if your usign AJAX you can cancel the default action by typing `.preventDefault()`
* example:
```js
// jquerry 
// Preventing a default action from occurring and stopping the event bubbling
$( "form" ).on( "submit", function( event ) {
    // Prevent the form's default submission.
    event.preventDefault();
    // Prevent event from bubbling up DOM tree, prohibiting delegation
    event.stopPropagation();
    // Make an AJAX request to submit the form data
});
```