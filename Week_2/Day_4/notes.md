# w2 - d4
## JSON
* JSON = javascript object notation
* a collection of name/values
* an ordered list of values
* they are universal data structures and almost all programming languages support them one way or another
* they look like this:
  ```js
  {
    "name": "New York City",
    "boroughs": [
      "Manhattan",
      "Queens",
      "Brooklyn",
      "The Bronx",
      "Staten Island"],
    "population": 8491079,
    "area_codes": [212, 347, 646, 718, 917, 929],
    "position": { "lat": 40.7127, "lng": -74.0059 }
  }
  ```
  * note: the keys are always double quoted "strings" and the values can be strings numbers or even objects
  * JSON syntax is and must be valid JS
  * when data is sent across the internet using http request/response the media type for JSON data is application/json whereas for a html document it's text/html. you can see this in the response header under content-type.

## serialization
* serialization is converting an object into a format that can be stored/transmitted between computers (typically a string of text)
* so ... :
  * serilization = Object --> string
  * deserilization = string --> object
* `JSON.parse()` = takes a string and turns it into an object
  * to use json.parse thestring must be in the right format. example: 
    * '{"a": 1, "b": 2}'
    single quotes around the curly braces and double quotes around each key
* `JSON.stringify()` = takes a JSON object and turns it into a string of text

## lecture notes
### exceptions
* exceptions are:
  1. type error
  2. reference error
  3. syntax error
* if js encounters 1 exception it will stop executing all code and return the error

### TRY and CATCH
```js
try {
  if(chicken) {
    console.log(chicken)
  }
} catch(error) {
  console.log(error)
}
```
* error.name = type/refernce/syntax error
* error.message = error message body

### promises
* promises are async
* promise is a constructor so it uses the `new` keyword
* it only take 2 parameters in its single callback
  1. resolve
  2. reject
* some promise methods are:
  1. `.then` if the promise resolves
  2. `.catch` if the promise rejects
  3. `.finally` does this regardless if the promise rejects or resolves
* you can shain promises like:
```js
Promise(a_promise).then(another_promise).finally(3rd_promise).catch(error)
```
  * this is useful when you are waiting for 1 API to resolve/reject and FINALLY call a second API and THEN have something or a CATCH for errors
* `Promise.all(promise1, promise2 ... )` is used when your promises are not connected to each other like posting the weather and retrieving all blog posts.. using this method will return an array of results.
* `Promise.race` is like `promise.all` except it takes the one that resolves first like when watching a movie online and using mirrors, it will chose the mirror that responds the fastest

### npx
* read more [here](https://blog.scottlogic.com/2018/04/05/npx-the-npm-package-runner.html) to learn about NPX which is kind of like NPM
