# w2 - we

Finish activities about promises on audacity

## tips for writing readable code
Links for writing readable code
https://github.com/airbnb/javascript

## cURL

* Curl is a command line utility that is used to make requests to a given url and it outputs the response. It allows you to see the url.

* cURL is a software package which consists of command line tool and a library for transferring data using URL syntax.

In the terminal type:
`curl [url] `
* This will give you the html of that url
* Including the flag `-I` will give you the response header

* If you want to save the data to a file that already exists on your local computer use:
`Curl [url] > [filename and location]`

* If you want to create a new file at the same time use lower case o flag
`Curl -o [myfilename.txt] [url]`

* If you don’t care about the local file name you can use capital `O` flag and it will create a file with the same name as that url resource:
`curl -O http://www.gnu.org/software/gettext/manual/gettext.html`

* You can chain curl `-O` and download resources from multiple webpages at once:
`curl -O http://www.gnu.org/software/gettext/manual/html_node/index.html -O http://www.gnu.org/software/gettext/manual/gettext.html`

* When a webpage has moved to a different name using curl `-O` will download text that only contains a location header like this:
```html
<TITLE>302 Moved</TITLE>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.co.in/">here</A>
```
… so if you want curl to automatically follow the link in the location header add the `-L` flag like this:
`curl -L http://www.google.com`

* If a download was stopped suddenly and you want to resume from where it was left off you can use the capital `C` flag with an extra dash to continue where you left off:
`curl -C- -O [url]`

* If you want to limit the rate of data transfer you can add a `limit-rate` flag like this:
`curl --limit-rate 25B -O [url]`
  * The 25B means 25btes but this can be whatever you want
  * Use `ctrl+c` to stop the download at anytime

* To DL a file only if its modified before/after a given date use the `-z` flag
  * `curl -z 21-Dec-11 http://www.example.com/yy.html` 
    * (this will check if its modified after 21 dec)
  * `curl -z -21-Dec-11 http://www.example.com/yy.html` 
    * (this will check before 21 dec)

* If a website you want to download from needs a username and password to view the resource you can pass the `-u` flag like this:
`curl -u username:password URL` 

* <strong>More [info](https://www.thegeekstuff.com/2012/04/curl-examples/) on cURL</strong>

## character encoding & character set

* The alphabets of every language is stored on every computer in what is called a character set. Each language has 1 unique character set. 

* Without having the proper character set a sentence might look weird to you. Having these characters set is like unlocking the cipher to the sentence and making it readable

* When your character can find the right font to display it will have a black square or question mark.

* Fonts are considered glyphs and once a computer knows what character set to use it will look up what that character is in the font. If the character set is wrong it will associate wrong characters to the font and display weirdly like a ransom note

* Utf-8 is the default character encoding. UTF-8 is the most widely used way to represent Unicode text in web pages, and you should always use UTF-8 when creating your web pages and databases.

* Utf8 is able to encode more than 1.1 million code points using 1 to 4 8-bit bytes

* Unicode = universal coded character set

* If you have a string, in memory, in a file, or in an email message, you have to know what encoding it is in or you cannot interpret it or display it to users correctly.

* Unicode is not a character encoding; it maps characters to numbers, but does not specify how those numbers are to be represented. it looks like this: `U+0065`

* ASCII is a fixed-width encoding, always using 7-bits to encode characters.

* UTF-8 is a variable-length encoding, using 1 to 4 bytes (most often 2 bytes).

* UTF-32 is a fixed-width encoding, always using 32-bits to encode characters.

## DNS

* DNS explained: [watch video](https://www.youtube.com/watch?time_continue=363&v=72snZctFFtA&feature=emb_logo)

### DNS record types
* There is a small subset that covers most case:
  * `A`: most common; map a hostnames to IP address (IPv4, 32-bit address)
  * `NS`: Name Server that is responsible for a DNS zone
  * `MX`: Mail Exchange record specifies where email gets sent to
  * `CNAME`: Canonical Name, an alias for another hostname
  * `AAAA`: similar to A, but uses IPv6, 128-bit address 

[Video](https://www.youtube.com/watch?time_continue=176&v=MZnSMexq1O0&feature=emb_logo) explaining record types 

* here are some cloud-based DNS providers:
  1. Amazon Route 53
  2. CloudFlare
  3. Verisign
  4. EasyDNS
  5. Azure DNS

* When going to a webpage there are 4 response/request stages:
  1. Root name servers “.”
  2. Top level domain “.com”
  3.  Name servers “google.com”
  4. Address records A (ipv4 address)
  * To test this out type in terminal:
    `dig +trace www.lighthouselabs.ca`

### DNS resolution sequence
* When performing DNS resolution the sequence of name servers that are queried are:
`Root —> TLD —> autoritative —> resolving`

## create server in node 
* Creating a server in node use this code:
```js
let http = require("http")
let server = http.createServer((request, response) => {
  response.writeHead(200, {"content-Type": "text/plain"});
  response.end("hello world its me XXX\n");
});
server.listen(3000)
```

* When making a request using nom request:
```js
var request = require("request");
	request("http://www.google.com",function(error,response,body)
	{
		console.log(body);
	});
```
## express and node
* express

* Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

* Express is one of the most used web frameworks in the Node community.

* Node actually functions as a JavaScript runtime, powered by Google's V8 engine (the same engine used to power chrome browser)

* Node essentially takes the place of the browser in the execution of js code

* node code looks liek this:
```js
const express = require("express")
const app = express();
const port = 3000;

// create a server on a local host like this
app.listen(port, () => {
  console.log("Server Running ....")
})

// making things happen at root of page "/""
app.get("/", (req, res) => {
  res.send("Hello World")
})

// create another web-page "/parks"
app.get("/parks", (req, res) => {
  res.send("The parks you've seen")
})
```