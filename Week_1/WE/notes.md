# weekend 1
## modules
* each file that node runs is considered a module
* using export is usually to export an object, and since a function is an object that works too
* by default node will export an empty object for each file
* the `node_modules` directory that holds all the packages taht support the package you installed should not be checked into git. it is a `.gitignore`

## how-to use
### export
```javascript
module.exports = sayHello;
```
* write this at the bottom of the .js file that actually has the sayHello function 

### require
``` javascript
const sayHello = require("./file")
```
* the above line has to be at the top of the .js file where you want to use it.
* there's no need to specify the file extension
* make sure its the coorect path. use `../` if the file is in an "upper" directory

## npm
* using `npm install [package-name]` will download that package to the current directory you're actually in.
* `npm init` will guide you to create a package.json file
* `npm install [package name] --save` will save the package as a dependecy in your package.json file, however npm now automatically does `--save` so there's no need to actually type `--save`

## package-lock.json
* it lists ALL the depencies (yours as well as all package's dependencies).
* do not modify this directly!!!
* using `npm install [package]` will indeirectly modify this for you
* package-lock.json and package.json should be checked into git
* the `node_modules` directory that holds all the packages taht support the package you installed should not be checked into git. it is a `.gitignore`

## package.json
* all node.js projects have a package.json file
* inside the json object you can add to the script key/property to run commands in terminal like `npm run myScript` , where `myScript` would be defined in the script key/property.
* [npm .json docs](https://docs.npmjs.com/files/package.json)
* package-lock.json and package.json should be checked into git
* the `node_modules` directory that holds all the packages taht support the package you installed should not be checked into git. it is a `.gitignore`

## semantic versioning
Given a version number MAJOR.MINOR.PATCH, increment the:
1. MAJOR version when you make incompatible API changes,
2. MINOR version when you add functionality in a backwards compatible manner, and
3. PATCH version when you make backwards compatible bug fixes.
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## manual/automatic testing
* unit testing
  * singling out your code in units to test if they pass
* integration testing
  * test to see if 2 separate parts of your code work well together. example: your code and the server
* functional testing: if the app as a whole works. how a typical user would navigate your app (happy path) and see if it works

* happy path is the path a user most likely would use your app, in other words the BEST CASE SCENARIO ... but you also need to test for the sad path, for the times the suer goes rogue or just simply might be bugs in your code for edge cases. example:
  1. wrong credit car number
  2. wrong address
  3. no stock left in inventory .... etc

## BDD: behavior driven development
* BDD frameworks:
  1. setup some data
  2. run code that should do something
  3. asserting that it does that thing

## how to use MOCHA and CHAI
* mocha is a library/package that allows us to run tests
* chai contains some useful functions to verify our test results.
* in a really bad anaology ... mocha is like the building where theres a gym, and chai is like the soccerball/volleyballs inside that make people have fun with. wow that was bad but you get it right??? :P
```javascript
const chai = require("chai");
const assert = chai.assert;
const expect = chai.expect;

const nameInverter = require("../nameInverter.js");

describe("#nameInverter", function() {
  // example test 1
  it("should return an empty string when passed an empty string", function() {
    const inputName = "";
    const expectedOutput = "";
    assert.equal(nameInverter(inputName), expectedOutput);
  });
  
  // example test 2
  it("should return a single name when passed a single name", function() {
    const inputName = "Eric";
    const expectedOutput = "Eric";
    assert.equal(nameInverter(inputName), expectedOutput);
  });
});
```
* `describe` is where you group all your tests into related groups and the `it` keyword is the single test that's nested inside the group









## side note
* to remove a folder in the terminal use `rm -rf [folderName]`
* r: recursively 
* f: forcefully (ignoring all messages)
* be careful!!!!!