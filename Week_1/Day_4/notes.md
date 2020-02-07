# day 4
* [teacher notes](https://github.com/Eric-Lombardo/lecture_w1d4_jan6)
* [teacher video](https://www.youtube.com/watch?v=VlT6pEuw-9Y&feature=youtu.be)

## functions
* in js functions are 1st class objects:
  * funcs can be stored in variables and passed around
  * funcs can doe verything that objects can do like having properties/keys assigned to them
  ```javascript
  const myFunc = function() {
    console.log("hello")
  }

  myFunc.name = "eric"
  console.log(myFunc.name) // returns "eric"
  console.log(myFunc) // returns an object with key/values
  ```
* functions take data as arguments like arrays, objects and variables, but when passing a function it's known as passing the reciever function a behavior
* function declarations get hoisted at the top versus function expressions which are not
* any function that doesn't start with the function keyword is a function expression

# higher order functions
* higher order functions is the function that can accept functions as a parameter. Remember its parameter and not arguments because functions describe an action, and parameters become arguments when a function is called
```javascript
  const myfunc = function() {
    // do something
  }

  const higherOrder = function(myfunc) {
    // do something with myfunc
  }
```
* methods such as map, filter and foreach are considered higher order functions because they take callback functions in their parameter
* calling a function is not unique to HOF because any function can do that. calling a function just simply means having many functions inside the body of a function and then calling/executing them whenever you want. REMEMBER HOF are HOF because they accept funcs as their parameter or returning them.


# anonymous functions
* they don't need to be named or even assigned to a variable. 1 time uses!
* even when assigning an anonymous function to a variable it doesn't suddenly get a name. it never has a name thus anonymous. what you are doing in that case is just ASSIGNING a variable the VALUE of the anonymous function definition, therefore the variable now has a function saved inside it but the anonymous function still remains what it once was ... anonmous lol.
``` javascript
  const greeting = (name) => "hello " + name
  // greeting holds the anon func
  // anon func is still only anon func

  c.log(greeting) 
  // returns an object with function as a key and anon func as value
  c.log((name) => "hello" + name)
  // returns anon func body

  // ======versus========
  function greeting1(name) {
    return "hello " + name
  }
  c.log(greeting1)
  // returns same object as c.log(greeting)
```
* all function expressions are anonymous like the one above.

# arrow functions
* for multi line functions they look like this:
```javascript
  (var1, var2) => {
    //do something
    return "hello" + var1 + var2
    // like any function if there's no return it returns undefined
  }
```
* if the function is 1 line long and has only 1 variable you can take out the curly braces and the parenteses arounf the variables and even take out the return statement liek this:
```javascript
  var1 => "hello" + var1
```
* functions don't have the use of the `this` keyword exactly ... it takes on the meaning of it's context. It will first try to find it in it's scope and if its not there it will look outisde and outside and once its in the global context and stillc ant find it, it will then return undefined.
* they are meant for short pieces of code that don't have their own "context" but rather work in the current one
* arrow functions can be used when using `new` beacause `new` is a constructor and constructors use the `this` keyword
* [fun fun function explains arrow functions on youtube](https://www.youtube.com/watch?v=6sQDTgOqh-I)

# callback functions
* a function passed (by reference) into another function (called the reciever)
  * the reciever function can perform the behaviour of the referenced function by calling it. this action is called a callback
  * the reciever can decide to call the callback func at any time and as many times, even return it
  ```javascript
  // The second argument/parameter is expected to be a (callback) function
  const findWaldo = function(names, found) {
    for (let i = 0; i < names.length; i++) {
      let name = names[i];
      if (name === "Waldo") {
        found();   // execute callback
      }
    }
  }

  const actionWhenFound = function() {
    console.log("Found him!");
  }

  findWaldo(["Alice", "Bob", "Waldo", "Winston"], actionWhenFound);
  ```
  * when passed in as an argument don't call it with parenthesis () or it will execute it right away. example: `waldo([1, 2, 3], action)`



# sort method
* when using the sort method keep in mind it converts every data into a string so for value types that are strings that's ok but it gets wierd when they are numbers for example.
```javascript
  let arr1 = ["b", "c", "a"]
  arr1.sort()
  c.log(arr1) // ["a", "b", "c"]

  let arr2 = [10, 1, 7]
  arr2.sort()
  c.log(arr2) // [1, 10, 7]
```
* it converts it to a string and then acts like a human dictionary and sees which comes first. This is known as lexigraphical sorting ... aka dictionary order
* so thats why sort accepts a callback function. this callback will evaluate 2 variables (a, b) and then use behind the scenes algorithms such as quick sort.
  * if a > b return 1 
  * if a < b return -1
  * if a === b return 0





# side-note
 * chaining terminal commands 
  ```javascript
  mkdir callback && cd callback
  ```
  * inside VS code when the folder is opened up you can press `cmd + p` to toggle a search query to quickly access files within that folder