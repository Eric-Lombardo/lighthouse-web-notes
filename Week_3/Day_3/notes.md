# w3 - d3
* [teachers notes](https://github.com/Eric-Lombardo/lhl-w3-express)

## HTTPS
* https encrypts request and response except for the headers

## labels
* use labels in forms for accessibility (screeen readers for the blind)
  ```html
  <form>
    <label for="username">username</label>
    <input type="text" id="username">
  </form>
  ```

## cookies
* everything in forms are stored in `request.body.[varName]`
* `response.cookie("[cookieName]", [value])`
* to fetch cookies by server `request.cookies.[cookieName]`
* to clear cookie `response.clearCookie([cookieName])`
### cookie session
* to create a cookie wuth npm cookie-session
  * `request.session.[cookieName] = "someValue"`

## VS Code tricks
* `cmd + shift + f`
  * this is like the normal `cmd + f` but it searches the entire project folder
