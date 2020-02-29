# w4 - d2
* [teacher notes](https://github.com/FrancisBourgouin/lectures-2020-mtl-feb03/tree/master/w4d2)
* [lecture video](https://www.youtube.com/watch?v=0INgRrl5uQ8&feature=youtu.be)

## Dom creation
* the HTML you write is parsed by the browser and turned into the DOM

## breakpoints in Code
* click [here](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints#overview) for when to use each breakpoint
* you can either set a breakpoint through chrome dev tools or directly in your code with debugger. it would look like this:
```js
console.log("a")
console.log("b")
debugger;
console.log("c")
```
* to set condtional breakpoints right click and choose "add conditional ..." Then enter your condition and press enter to activate it. These will show in orange

## getElementsByTagName
* the HTML collection returned by `getElementsByTagName` is not really an array (they are array like) so you need to convert it into an array to have access to all the array methods `Array.from(htmlCollection)`
* when using `removeEventListener` you need to remove the "named" callback so if it's anonymous it won't work, it needs to be named (stored in a variable)

## event handlers
* when using event handlers make sure to use es5 syntax for functions and not ES6 "fat arrow" syntax or else `this` will refer to the window and not the target element
* `$(document).ready()` fires as soon as the DOM is ready vs. `window.onLoad` only fires after all images and other resources have loaded