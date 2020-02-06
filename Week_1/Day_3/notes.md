# Day 3 notes
# [teacher's Notes](https://github.com/Eric-Lombardo/lhl-w1d3)

## primitives
* types
  * undefined
  * null
  * string
  * number
  * boolean
  * symbol (introduced in ES6)

## objects
* objects are not primitive data types because but they can hold all primitive data types
* arrays and functions are subcategories within objects
* object literal syntax example:
```javascript
  const emptyObj = {
    key: "value",
  }
```
* when using [braacket] notation for objects the key inside the brackets MUST be a string literal chich means it must have quotes around the key, otherwise it thinks it's a variable and if the variable is not defined elsewhere in the code there will be a reference error. BUT if that variable points to a variable that is a string THEN thats okay!

Examples:
```javascript
  const person = {first: "eric"};

  person[first] // is bad
  person["first"] // is good

  //////// another example below //////

  // when you want to use bracket notation but the key doesn't exist yet, you need to surround it in quotes and then assign it a value.
  obj["key"] = "value"  
```

* object keys are always strings but for convienance they are ommited when defining them when creating an object literal. BUT if the key has spaces, hyphens or periods than quotes are needed!!! `{"my-hyphenated-key": "value"}`
* instanceof method tests if a certain object is an instance of a specific constructor. it is used like this `[object] instanceof [constructor]`
an example:
```javascript
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// expected output: true

console.log(auto instanceof Object);
// expected output: true
```
* objects in Js are the same as hash, hashtables, dictionaries, maps or associative arrays in other languages.
* if you want to see all keys within an object use: `Object.keys(objectNameToBeChecked)`
* in objects, keys and properties are interchangeable terms.

## for ... in loops
* for ... in loop is a way to loop over an object's keys. 
```javascript
  const planetMoons = {
    earth: 1,
    mars: 0,
    jupitor: "i dont know"
  }

  for (let planet in planetMoons) {
    // planet is any variable name we choose
    // do something with each item
  }
```
* there are limitations with the for ... in loop. For example objects inherit methods from their parent so to make sure the iterator (in this case the iterator is "planet") is actually in the object we want to loop over use at the top of your for ... in loop.
```javascript
  const planetMoons = {
    earth: 1,
    mars: 0,
    jupitor: "i dont know"
  }

  for (let planet in planetMoons) {
    if (planetMoons.hasOwnProperty(planet)) {
      // do something with each item
    }
  }
```



## side notes
* Use null if needed and leave JS to use undefined, this way if ever something is returned undefined you know its an error and not something that you assigned to being undefined.

