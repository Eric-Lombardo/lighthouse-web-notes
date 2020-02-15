# w2 - d5
## Object oriented programming
* OO is a software paradigm just like how functional programming is another software paradigm
* OO is a popular way to organize, re-use and have modularity to your code
* JS is not stricly OO but can be. In fact JS initially popularized functional programming
* in OOP we use objects to group related variables and functions together
* key/value pairs are known as properties
* when the value of an object's key is a fucntion it's called a METHOD. any other value is is called the object's STATE.

## methods
* if an object has a method we say that the object has a behaviour
* methods are names of functions that are tied to objects
* when you use `this` inside of a method, `this` referse to the object that the method was called on.


## quick recap
1. objects are bundles of information
2. it's not just information (aka STATE)
3. it has tuff it can do (aka BEHAVIOR)
4. typically these behaviours take the form of METHODS, which are just named functions
5. some methods modify the object
6. some methods ask the object for information

## class
* class: is like a blueprint of a house
* objct: is the actual house that was built using the blueprint
* this is how the class syntx looks liek:
```js
class Pizza {
  // add default values here
}

// always capitalize
// should be a noun
```

```js
let pizza1 = new Pizza
let pizza2 = new Pizza
```
* now pizza1 and pizza2 are instances of the class Pizza
* even though pizza1 and pizza2 are built using Pizza they are still 2 completly different objects. much in the same way that 2 houses built by the same blueprint are still 2 different sperate houses.
* making a class you don't need to use semi-colons or commas to separate default values or methods.
```js
// no commas or semicolons
class Pizza {
  constructor() {
    this.toppings = ["cheese"];
  }

  addTopping(topping) {
    this.toppings.push(topping);
  }
}
```
* methods inside a class can't be accessed by the class itself, only the instance objects can use the method

## constructors
* constructors are a way to give any of the instance objects default values 
* an example of when you want to pass default values: 
``` js
// constructor arguments
class Pizza {
  constructor(sauce, style) {
    this.sauce = sauce;
    this.style = style;
    this.toppings = ["cheese"];
  }

  addTopping(topping) {
    this.toppings.push(topping);
  }
}
```

## supercalss
* if 2 classes (aka blueprints) share the same code you can create a super class to add that shared code in to DRY up your code
```js
              Person(superclass)
              /               \
            /                  \
      Student(class)          Mentor(class)
```
* Student and Mentor are now sub-classes of Person
* the sytax for subclasses to connect to a super class is like this:
```js
class Student extends Person {
  // stuff goes here
}
class Mentor extends Person {
  // stuff goes here
}
```
* In your JS file a superclass always ahs to be on top of all of its subcalsses or it will throw an error

## method overriding
* when a sub-class implements a method that already exists in the superclass it's called method overriding. The sub-class's method will take precendene
* you can also use the `super` keyword to access methods or default values from a class's superclass

## GET and SET
* the GET and SET keywords converts methods into values and can be used to compute on the fly. They just make an objects  interface cleaner.
* here's an example:
```js
class Pizza {
  constructor(sauce, style) {
    this.sauce = sauce;
    this.style = style;
    this.toppings = ["cheese"];
  }

  addTopping(topping) {
    this.toppings.push(topping);
  }

  set size(size) {
    if (size === "s" || size === "m" || size === "l") {
      this._size = size;
    }
  }

  getSize() {
    return this.size;
  }

  get price() {
    const basePrice = 10;
    const toppingPrice = 2;
    return basePrice + (this.toppings.length * toppingPrice);
  }
}


// testing
const pizza = new Pizza;
console.log(pizza.price);
console.log(pizza.size = "s");
```
* a GETter can help validate proper responses and/or reject bad ones. for example:
```js
inputs "s", "m", "l" are proper/accepted responses for this app

inputes "small", "medium", "large" are not accepted by this app
```

## dependency injection
* dependecy injection means passing an object the things it needs rather than having the object access them itself

## OOP best practices
1. prefixing a key with an underscore `this._toppings` is a way to tell other developpers looking at your code that you shoudln't access these keys directly. they've been abstracted away
2. single responsibiltiy: each class should be responsible for only 1 thing so if theres a change to be made it won't affect everything else.