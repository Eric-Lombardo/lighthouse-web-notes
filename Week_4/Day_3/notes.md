# w4-d3
* [teacher notes](https://github.com/Eric-Lombardo/lhl-w4d3)

## Ajax
* ajax requests don't interupt a user's interaction with the current web page. instead of the http request replacing the webpage in the browser it is passed to a JS function and that function is responsible for determining what to do with it. often the JS will modify the DOM to reflect the response from the server
* it is used to get data from the web server into strings for JS
* commonly these are JSON strings so that they can be converted into JS object. this is so common that jquery will do string --> object conversion if it can tell that the data is JSON. what you do with that data is up to your imagination
* browsers will give error messages if things go bad but with AJAX you need to code all those circumstances to fix errors on your own

### more about Ajax
This is a valuable workflow because it makes web pages more dynamic by allowing subsequent requests to be sent to the server without navigating away from the page. In traditional, synchronous web sites, each time a user clicks a link or submits a form they have to wait for the server to send the next web page for them to interact with (after the browser has rendered it). Ajax allows the user to continue using the web page while the request-response cycle is done in the background, asynchronously.

### how Ajax works
Ajax requests are normal HTTP requests sent to a web server by some JavaScript on a web page. A lot of the time these requests are made after the user interacts with the page in some way, like clicking a button. In fact, the way that you tell JavaScript to run some function when a button is clicked is very similar to the way that you tell JavaScript to run some function when an HTTP request returns.

## JQuery for AJAX
* JS is capable of making AJAX requests without any code libraries but JQuery is one library that improves how AJAX is done in JS
* you can use `$` as a function like `$(".class")` where class is a parameter or you can use a method on the `$` object like `$.ajax()`

## preventing XSS cross site scripting
* when a user types `<script>alert("hacked")</script>` as a tweet or username your html will intrepret it as an actual script and cause chaos. so instead of trusting user input you should sanitize the input by `$("<div>").text("hello")`
  * create a new element with jquery and then use the etxt method which treats the string as just characters so `<script>` actually just becomes the string `"<script>"` and not actually a script tag

## side-note 
* npm http-server is a simple Node server to try things out. Check it out [here](https://www.npmjs.com/package/http-server) 