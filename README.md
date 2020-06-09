# Add a request method to connect app useful for testing app.

## Installing

````
npm install connect-mock-request
````

## How to use ?

````javascript
var request = require('connect-mock-request'),
    connect = require('connect'),
    app = connect()
          .use(function (req, res) {
            res.end('Hello world !');
          });

request(app)
.get('/')
.end(function (res) {
  console.log(res.body); // Hello World
});
````

## API

### request(method, path)

Execute a request using a method and a path.

````javascript
request(app)
.request('post', '/')
...
````

#### Aliases

All of these methods are avalaible via alias :

* GET
* POST
* PUT
* PATCH
* DELETE
* HEAD

````javascript
request(app)
.patch('/')
...
````

### set(name, value)

Set a header.

````javascript
request(app)
.set('Content-Type', 'application/json')
...
````

### write(data)

Write body data.

````javascript
request(app)
.write('{"user": "greg"}')
...
````

### end(callback)

End the request.

Callback takes a single `response` argument which contains all response attributes and a `body` attribute.

````javascript
request(app)
.get('/')
.end(function (res) {
  console.log(res.body);
});
````
