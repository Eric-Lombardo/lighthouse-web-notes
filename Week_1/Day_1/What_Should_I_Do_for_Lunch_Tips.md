# Tips

Try experimenting with the comparison operators (`<`, `>`, `===`, etc.) in the node REPL, which you can launch using the `node` command in Vagrant.

Work on your code iteratively – that means in small pieces. 

To help you figure out how to use `hungry` and `availableTime` inside your function, try outputting their values to the Terminal as follows.

``` JavaScript
function whatToDoForLunch(hungry, availableTime) {
  console.log("hungry is", hungry);
  console.log("availableTime is", availableTime);
}
```

# RECAP

When using node.js in the terminal you can get an array of given arguments like this:

* First this is what you would write in the terminal:

``` Javascript
node [fileName].[extension] [argument 1] ... [argument n]
```

* Then inside your text editor you can retrieve all arguments by doing this:

``` Javascript
const argumentArr = process.argv
```

* keep in mind that every argument thats put in node is typeof string! So even if the argument is 3 (typeof Number), in the argument array it will be "3" (typeof String). In order to re-convert the string back to a number use: `parseInt()` with a base of 10 for decimal integer.

* Also, this argument array comes with some extra elements at the beginning of the array:
  * 1st element: The location where node is installed.
  * 2nd element: the file name.
  * 3rd element to n-th element: actual arguments passed in node.

  Use Array.slice method to just keep a copy of the array starting at index 2 to get a full list of arguments like this:
  ```Javascript
  const argumentArr = process.argv.slice(2)
  ```

* Don't make git repos inside other git repos!
  * steps to get a git repo:
    * `git init` in directory
    * create a new repo on Github and copy the SSH link.
    * `git remote add origin [url-link]` in directory
    * then the usual: 
      * `git add [file name]`
      * `git commit -m "message"`
      * `git push origin master`

  * Differences between forks and clones:
    * forks: copies the existing repo from the server to your github account.
    * clone: copies the repo from your personal github account locally to your machine.
      * steps to clone:
        * After forking a repo, copy the SSH key.
        * in terminal and inside directory type:
         ```Javascript
         git clone [ssh-key] [customized-name]
         ```
         If no customized name is given the folder created in this directory will be a loooooong randomized string. If you forgot to give a name and you want to just delete the folder you created by typing this:
         ```Javascript
        rm -rf path/to/your/gist/directory
         ```
* Using ESLint:
  * anywhere in terminal type:
    * `npm install -g eslint`
  * for specific all-ready-made configurations you can download them directly so that ESLint uses these rules/guidline by typing this:
    * `curl -o /vagrant/.eslintrc.json https://gist.githubusercontent.com/kvirani/6cdb9511522d4357839718a050e7dd3b/raw/.eslintrc.json`
      * curl -o: CL command to download file
      * 1st part: a location locally where this configuration file should be dowloaded to.
      * 2nd part: the actual link of where curl should go to download the configuration file.
  * Once installed you can run ESLint to see any errors by being inside the directory where the .js file is, that you want to check for. Type this once inside that direectory:
    * `eslint [filename and extension]`
    * or if its the only file there: `eslint .`

# General Thoughts
* I expected the first day to be relaxed but I'm super thankful to have put alot of hours of prep before startin the bootcamp because I honestly think if I didn't today would have been quite a stressful day! Looking forward for tomorrow's lesson! 