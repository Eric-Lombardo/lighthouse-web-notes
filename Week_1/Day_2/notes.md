# day 2 notes

## for ... of loops
  * you can do this with  arrays strings and objects. Even nesting them like you would with a traditional for loop. It's a good alternative if you don't need to use the index number that a normal for loop would have available.
  ``` Javascript
  for (let element of arr) {
    console.log(element);
  }
  ```

## cmd + alt + arrowkey(left or right) 
* allows you to cycle through chrome tabs in the same window. this also works with tabs open in VS code.

## focal 
* at LHL stands for:
  * functions
  * objects
  * conditions
  * arrays
  * loops

## side-note 
* during today's lecture we were asked why we were interested in learning to code. It might sound wierd but it's like how witches say some cool incantation in some wierd language and if everythign is right something magical happens. Thats how i see coding. Speak and write in a computer language and suddenly you can control your lights in the room to shut off. MAGIC! and thats why i want to learn how to code, to do cool things like that.

## algorithms
* with algorithms a cool analogy was mentioned. If you make muffins but forget to add sugar, in the end you still made muffins but they don't taste good. With code it's not like that. Everything needs to be done in a certain way and in a certian order or else you get nothing at all, whereas with muffins you can mess up a little and still get something.

## process.exit()  
* when you call process. exit() you actually emit the exit event that ends all tasks immediately even if there still are asynchronous operations not been done. In some ways it's like return ... i think.

## function names and more
* a good function name is:
  * short
  * explains exactly what it does
  * unambiguous
  * data needed by functions shoudl be passed in as parameters instead of using a global variable directly.

* name your functions with action words like: createUser or sendUserData
* always adapt to the current team's convention
* each function should focus on a specific task
* a function can be either a pure function (returns a value) or be a side-effect function
* split a function into smaller functions if that function is doing 2 or more things

## reading error messages
* syntax error: unexpected token
  * usually means a parenthesis, bracket or curly brace is missing
* reference error: [blank] is not defined
  * a spelling mistake or trying to use a value of an undefined variable
* type error
  * undefined is not a function. check spelling of your function and/or spelling of method names

## truthy and falsey
* everything is turthy in JS except for these things which are falsey:
  * false
  * 0
  * "" empty string
  * null
  * undefined
  * NaN