# w3 - d4
* [teacher notes](https://github.com/Eric-Lombardo/lectures-2020-mtl-feb03/tree/master/w3d4)
* [course video](https://www.youtube.com/watch?v=ZtKGbiUgqJI&feature=youtu.be)

## REST
* representational state transfer
* this is a style so it's not enforced but here are some guidelines:
  1. client-server independence, which means it should work for everyone and not use specific methods that not everyone ahs access to
  2. stateless: each route oesn't depend on previous routes
  3. cacheable: webpages should be able to be cached on client's computers
  4. uniform interface (consistent style) like having urls built in a logical pattern

## cleaning up GET POST routes on a server.js file
* adding many post and get routes ona  server.js file can make that file super long and especially grows larger when you start adding specific routes like: `domain.com/posts/:postid/comments/:commentsid` so you can add modularity to split routes
* in server.js:
  ```js
  app.use("/posts", postRouter)
  ```
  * where postRouter is a variable name that points to a separate file
* in postRouter file:
  ```js
  postRouter.get("/", (req, res) {
    // do things
  })
  ```
  * it will understand that `"/"` actually means `"/post"`
* dont forget module.exports in postRouter and require in server.js

## middleware
* when using middleware the order of how you use them (`require([npm Name])` and `app.use()`) in server.js file 