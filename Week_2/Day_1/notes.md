# w2-Day 1

[teachers notes](https://github.com/Eric-Lombardo/lectures-2020-mtl-feb03)

[class video](https://www.youtube.com/watch?v=55QyCARbj_8&feature=youtu.be)

## test driven development
* otherwise known as TDD where you test first

## using mocha/chai
* `const { expect } = require.("chai")` is the same as"
``` javascript
  const chai = require("chai");
  const expect = chai.expect;
  // this is called object destructuring
```
* in testing the term regression is when one test passed but after adding more code those same tests start failing

## requiring
* when using `const var = require("./function.js")` you have access to EVERYTHING that `function.js` has access to. example other functions in that js file and all global variables etc.

## object property shorthand
``` javascript
let cat = "meow";
let dog = "woof";

let obj = {
  cat,
  dog
}

console.log(obj)
// logs out
// {cat: "meow", dog: "woof"}
```

## side-notes
* `.include()` is like using `typeof`
