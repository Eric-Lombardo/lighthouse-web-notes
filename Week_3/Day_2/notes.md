# w3 - d2
* [teacher notes](https://github.com/Eric-Lombardo/w3d2-lecture-feb3)
* [video recording](https://www.youtube.com/watch?v=poXIZPk84DQ&feature=youtu.be)

## nodemon
* nodemon is a utility that will monitor for any changes in our source code and automatically restart our server

## quick reminder of NodeJS
* node js is a runtime JS that allows to be run outside of the browser, namely on the server and it includes HTTP libraries but it's not reallly considered a framework, like Express is.

## quick reminder of express
* when using `res.render("[file.ejs]")` it must be a file that's inside a `views` folder because by default `res.render` will look for a directory names `views` and then render out the corresponding `ejs` file that you specfiy inside the aprenthesis

## forms
* a form needs a name attribute to create a key in `req.body` for body-parser to give back the user's input data:
```html
<form>
  <input type="text" name="quote">
  <input type="submit">
</form>
```
* so now when the user fills out the `input type="text"` with whaetever he wants (example: "why so serious") and then clicks the `input type="submit"` button, body-parser (using `req.body`) will now create an object that looks like this:
```js
{quote: "why so serious"}
```

* forms only accept the HTTP methods `POST` and `GET`

## side-notes
* JSON.stringify will show nested objects in node

## git branch
* to create a git branch type:
  * `git branch [feature/display-name-colors]`
    * you can name whatever you want inside the square brackets, just dont actually include the square brackets :P
* now if you want to merge the branch back to the master branch type:
  * `git checkout master`
  * `git merge feature/display-name-colors`
* click [here](https://web.compass.lighthouselabs.ca/days/w03d2/activities/673) to go to the compass assignment that talks about this.
* click [here](https://learngitbranching.js.org/) to play an interactive game to learn about git in general (including branching)
* click [here](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) to read about branching in a nutshell

## cookies
* diagram explaining of cookies work:
* browser ------------------------------  server
* ------------- request webpage -------------->
* <------------COOKIE + wepage response -------
* ----- ask another page + attach COOKIE ----->
### to see cookies in browser
* to see cookies in the browser open up chrome dev tools and under the "application" tab you can see a cookies dropdown.
* to delete the cookies right click on the actual cookie and press `clear`