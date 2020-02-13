# w2 - day3
## `net` module
* the (net) is a module that is built in Node so it'll allow node apps to use TCP

## creating a server
* to create a server:
  1. rewuire net
  2. create server with net.createServer
  3. on connection event
  4. handle data coming from the client
  * (item 3 and 4 can be nested inside each other)
  5. listen to specific port
  * look at these [events](#events)
  
<strong>The server is always running so it's the client that establishes the connection much like how someone calls a hotline/company. the client needs an ip address and a port to connect (for the analogy it would be a company telephone number and an extension number)</strong>
``` javascript
// boilerplate for server
const net = require("net");

// create server
const server = net.createServer();


//send message after a connection is made
server.on("connection", client => {
  console.log("new client connected!!");
  client.write("Hello there!");

  // to handle data coming from the clients
  client.setEncoding("utf8");
  client.on("data", data => {
    console.log("Message from client: ", data);
  })
});

server.listen(3000, () => {
  console.log("Server listening on port 3000!");
});
```

## creating a client
* to create a client:
  1. require net
  2. create connection using `net`
  3. set encoding
  4. conn.on("data", callback) to handle data from server
  5. send message to server using conn.on("connect", callback)
  * look at these [events](#events)


<strong>The server is always running so it's the client that establishes the connection much like how someone calls a hotline/company. the client needs an ip address and a port to connect (for the analogy it would be a company telephone number and an extension number)</strong>
  ``` javascript
  const net = require("net");
  const conn = net.createConnection({
    host: "localhost",
    port: 3000
  })

  conn.setEncoding("utf8");

  // to recieve data from server
  conn.on("data", data => {
    console.log("Server says: ", data);
  });

  // to send a message to server on connection event
  conn.on("connect", () => {
    conn.write("Hello there from client!");
  });

  ```

## lecture notes
* TCP = stands for Transmission Control Protocol/Internet Protocol, which is a set of networking protocols that allows two or more computers to communicate. <strong>It will never lose a packet</strong>
* UDP = User Datagram Protocol (UDP) is part of the Internet Protocol suite used by programs running on different computers on a network. UDP is used to send short messages called datagrams but overall, it is an unreliable, connectionless protocol. <strong>Doesn't care if packest are lost, like a twitch stream</strong>
* what are ports?
  * 65 000 ports per pc
  * think of ports lke a boat pier
  *if you use a port that's already in use it will tell you to go away
  * over pot 9000 no one really uses those so you'll connect right away


## TCP
* TCP is language angonstic which means a JS app can communicate with a python app. most programming languages offer an interface like `net` to establish TCP

## events
* a data event is to handle ncoming data and it looks like this:
``` javascript
conn.on("data", callback)
```
* a connect event is triggered as soon as a connection is established and looks like
``` javascript
conn.on("connection", callback)
```

* for a server to write to a client its `client.write` when client is in the argument of the callback function:
``` javascript
(client) => client.write("msg")
```

* for a client to write to server its:
``` javascript
() => conn.write("msg")
```

## http
* hyper test transfer protocol.
* hyper text = is text taht links to other texts
* http is the protocol for the world wibe web
* http and tcp are different protcols bt they work together
* http is a protocol to read/write "resources" (data) of text like JS files, CSS files, HTML files
* http is a request/response based porotcol. a client makes a request to a http server that contains the specific resource we want and the server responds with a text based response
* is the "language" that both client and server use to communicate over a TCP connection
* come famous ports:
  1. HTTP port 80 usually
  2. HTTPS port 443 usually

## error codes
* 302 status code is a redirect
* 2xx is for a success
* 4xx is for client error
* 5xx is for server error


## requests
* an operation a client wants to perform. some examples are:
  1. GET: gets a resource
  2. POST: post a resource
  3. TRACE: performs a message loop-back test along the path to the target resource, providing a useful debugging mechanism.
  4. DELETE: equests that the origin server delete the resource identified by the Request-URI. This method MAY be overridden by human intervention (or other means) on the origin server.
* a header field looks like this:
``` js
// user-agent
Mozilla/4.03 [en] (WinNT)
```
## NPM request
``` js
const request = require("request")
request("http://www.expamle.com/eric.html", (error, response, body) => {
  console.log("Error: ", error);
  console.log("Response: ", response && response.statusCode);
  console.log("body: ", body);
})
```

## responses
* they consist of:
  1. the http protcol they follow
  2. a status code ex: 200
  3. a status message like "ok" 

## URLs
* check this [link](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL) out to see all the aprts of a url
* check this [link](https://web.compass.lighthouselabs.ca/days/w02d3/activities/192) for the compass assignment for more instructions
* implicit protocol:
`//developper.mozilla.org/index/cats` As you can see we did not sue HTTP or HTTPS at the beginning. the browser will use the same protcol as its parent document

## data flow when accessing a webpage
whenever we try to access a webpage we:
  1. open a TCP connection between us and the HTTP server's IP address
  2. we make a HTTP request via text based commands like `GET`
  3. wait for a response from the server 



