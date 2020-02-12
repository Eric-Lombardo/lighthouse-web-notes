# w2-day2
[teachers notes](https://github.com/Eric-Lombardo/lhl-w2d2)


## asynchronous
### general
* async programmins is when a unit of work is run separately from the main thread of the program and notifies the program of it's completion
* I/O (input/output) are time consuming. some examples of this are: reading/writing to/from disk or network
* JS leverages callbacks in order to deal with time consuming tasks.
* callbacks are a common way to handle async flow
### getting abck data
* if you need the data that an async fucntion will give (like retrieving data from a server) you cannot just return the data, you need to pass the data into a callback that returns taht data.
```javascript
// asyncBreeds.js
const fs = require('fs');

const breedDetailsFromFile = function(breed, callback) {
  console.log('breedDetailsFromFile: Calling readFile...');
  fs.readFile(`./data/${breed}.txt`, 'utf8', (error, data) => {
    console.log("In readFile's Callback: it has the data.");
    // ISSUE: Returning from *inner* callback function, not breedDetailsFromFile.
    if (!error) callback(data);
  });
  // ISSUE: Attempting to return data out here will also not work.
  //        Currently not returning anything from here, so breedDetailsFromFile function returns undefined.
};

const printData = function(data) {
  console.log("Return Value: " + data);
}
```

## setTimeout
* setTimeout uses a callback as the first parameter and a delay in milliseconds
```javascript
console.log('first line');
setTimeout(() => {
  console.log('timeout line');
}, 1000);
console.log('last line');
```
* some examples to use setTimeout:
1. Some sites will show a notice to the user and then automatically hide it after a few seconds. That's accomplished via setTimeout
2. In Gmail or other web-based email clients, a yellow "disconnected" message popus up at the top if we go offline. It usually indicates that it will retry to connect after x seconds. This countdown and its retry is implemented using setTimeout.
3. Some websites like to pop open an in-browser chat button after a few seconds. setTimeout is used to make them appear with a short delay.
4. If you use an Adblocker browser extension, you've likely seen prompts from websites asking us to disable them for that site. These don't come up right away and instead are delayed by a few seconds. The delay here would be implemented using setTimeout.
* setTimeout is a good way of handling heavy operations such as:
1. reading/writing
2. downloading/uploading


## lecture note
### functions
* functions are first-class beacuase:
  1. can be assigned to any value
  2. pass them as arguments into other functions
  3. functions are technically objects
### async logic flow
```javascript
main JS script | Event loop 
               | (wait for the async to be done)
               -------------------------
               | ready area
               | (wait for main JS to be done to pass these in)
```



## stdin/stdout
* `const stdin = process.stdin` input from user to the terminal
* `const stdout = process.stdout` output that terminal will spit out
* console.log() prints everything to a new lne. it's basically doing `\n`. If you dont want a new line you can use:
`process.stdout.write(" ")` and it will place everything on one line.
* in stdout
  1. `\n` is newline
  2. `\r` places cursor to the beginning of the line

## events
* events stay in the event loop for re-use unlike setTimeout which is a one time use and will leave the event loop once its ready
* some event examples:
  1. click a button
  2. click a button
  3. submit a form
  4. click and drag something
* to see a diagram of how a stdin/stdout looks like download the image [here](https://d.pr/i/yq3N95+) 
* an event example:
```javascript
const stdin = process.stdin;
// don't worry about these next two lines of setup work.
stdin.setRawMode(true);
stdin.setEncoding('utf8');

////////////
// Event Handling for User Input
////////////

// on any input from stdin (standard input), output a "." to stdout
stdin.on('data', (key) => {
  process.stdout.write('.');
});

console.log('after callback');
```

## side-notes
* node debug feature allows you to step through your code. figure out how to use `node inspect`
* `npm init -y` will avoid asking you all the questions to make a package.JSON and assume yes at the end. thats whay the `-y` means.
* when testing async functons in mocha and chai you need to use `done()`
