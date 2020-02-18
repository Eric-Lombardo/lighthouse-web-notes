# w3 d1
* [teachers note](https://github.com/Eric-Lombardo/w3d1_2020-02-17)

## url shortener
* url shortener is a service taht takes a regualr URL and transforms it into an encoded version which redirects back to the original URL.
  * www.lighthouselabs.ca --> goo.gl/6x7c

## stateful and stateless
* stateful: is when the server keeps in memory of where you are like accessing folders in a FTP server
* stateless: when the server doesn't have any memory/concept like HTTP request/response

## request header
```js
  host: emilecantin.com
  user-agent: none
```
* user-agent is just a fancy word for client, in this case the client is the browser

## node server
```js
  response.write("blah blah") 
  response.end("blah blah")
  // in browser it'll show blah blah
```
* anything after `.end` will not execute and throw an error.

## express variables
```js
  /sayHi/:name
```
* `:name` is the variable and variable name, and liek variables you can name it whatever you want.
* now the user can write whatever he wants after `sayHi/` and the next word will be saved in the `:name` variable.
* you can access these params by `req.params.name`
  * so... `sayHi/eric`
  * `req.params = { name: "eric" }`

## express queries
* `url/?name=yo&hello=hi`
* you can access the query object by typing `req.query`
  * using the above example the `req.query` equals: `{name: "yo", hello: "hi"}`

## app.use
* `app.use` is a middleware that gets called for every request
* the syntax:
  * `app.use((req, res, next) => next())`
   1. `.use` when you dont care what HTTP method to sue
   2. `next` and `next()` is there because if it's not it will cause your server to hang/block and not be able to conitnue the rest of your script

## HTTP methods (verbs)
* common HTTP verbs:
  1. GET
  2. PUT
  3. POST
  4. DELETE

## cookies
* a cookie is sent with every request.
* every subsequent request your computer shows that cookie and autheticates you.
* the HTTP protocol is stateless but the cookie injects the "state" so that the server can remember you because the server IS stateful.

## EJS in Express
* `app.set("view engine", "ejs")`
and then ...
* `app.render("[filePath and name]")`
* you cant send .html files in express because you're writing JS in express so you need to use EJS (embeded JS) which you can embed .html code inside a JS wrapper

## EJS tags
* `<% ... %>` everythign inside can be normal JS
* `<%= ... %>` stores variable values
  * these correspond to the local variables for example: `:name` from `req.params.name`
* `<%- include("[filepath and name]")  %>` for when you want to include templates/partials in EJS
* naming a file `_header.js` signifies that it's for a partial

## templates
* templates are files that define the presetnatation of the web app's data separetly from the server logic. basically if you want to write html code you need to write it in a different file than the `createServer` file
* Why are templates helpful?
  1. Keeping server logic (in this case JavaScript) separate from markup (HTML), making it easier to modify or debug one without affecting the other
  2. Separating different parts of an HTML document into different files, helping keep the length of HTML files short and manageable
* when sending variables to an EJS template we need to send them inside an object even if we are only sending 1 variable.

## side-notes
* there's no need to restart the server if nothing was changed on that file
* express is a routing middleware
* EJS is evaluated on the server side before the HTTP response is sent to the client

## CRUD
* all web apps allow users to amnipulate data in various ways. these can be broken down:
  1. C create = add a new record
  2. R read = retrieve the value of the record
  3. U update = update a record's value
  4. D delete = delete a record

## database
* we use DBs to store data because it allows the data to be persisted. this emans it won't dissapear when we restart our app's server.
* click [here](https://web.compass.lighthouselabs.ca/activities/167#text) for a diagram of how a client-server-DB works

## HTTP methods (verbs) and corresponding CRUD
1. GET = READ
2. PUT = UPDATE
3. POST = CREATE
4. DELETE = DELETE

## safe and unsafe methods
* get, head, options, trace are safe because they only retrieve resources without causing side-effects on the server
* post, put, delete, patch by contrast may cause side-effects on the server
* click [here](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Summary_table) for a HTTP summary table

## idempotent
* this means that making multiple identical requests should have the same effect as a single request
* put, delete, get are idempotent
* post is NOT because sending multiple identical requests affect state or cause side-effects like multiple financial transactions when the user doesn't know that his first equest worked.  
* click [here](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Summary_table) for a HTTP summary table

## forms
* the `action` attribute tells the form which URL to submit to
* the `method` attribute tells the form which HTTP method to use
* the `input` tag also has an important attribute `name`. this identifies the data we are sending. in this case below, it adds the key `longURL` to the data we'll be sending in the body of the post request
```html
<form class="form-inline" action="/urls" method="POST">
  <div class="form-group mb-2">
    <label for="longURL">Enter a URL:</label>
    <input class="form-control" type="text" name="longURL" placeholder="http://" style="width: 300px; margin: 1em">
    <button type="submit" class="btn btn-primary">Submit</button>
  </div>
</form>
```

## routes
* routes should be ordered from most specific to least specific
```html
  /urls/new           // first
  /urls/:shortURL     //second
```
* or else `:shortURL` might think `new` is a parameter and not a separate page

## body-parser
* body-parser npm will convert the request body from a buffer into a string we can read. it will then add the data to the req object under the key `body`