# HelloNode.js
Getting started Node.js

### Install Node.js & npm(package manager)

  curl -sL https://deb.nodesource.com/setup | sudo bash -
  
  sudo apt-get install nodejs
  
  sudo apt-get install build-essential

  sudo apt-get install npm

### Create Empty Project

Create a file "app.js"
```
// This application uses express as web server, see: http://expressjs.com
var express = require('express');
var app = express();
var bodyParser = require('body-parser');

app.use(function(req, res, next) {
	res.set("Access-Control-Allow-Methods","POST, GET, DELETE, PUT");
	res.set('Access-Control-Allow-Origin', '*');
	res.set('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
    next();
});

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

var fs = require("fs");

// Make files in ./public accessible
app.use(express.static(__dirname + '/public'));

// start server on the specified port
app.listen(process.env.PORT || 80, '0.0.0.0', function() {
	console.log("server started");
});


app.get('/',function (req, res) {
	fs.readFile( "index.html", 'utf8', function (err, data) {
		res.end( data );
	});
});

```

Create a file "package.json"
```
{
	"name": "testhtml",
	"version": "0.0.1",
	"private": true,
	"scripts": {
	"start": "node app.js",
	"test": "mocha"
	},
		"dependencies": {
		"body-parser": "1.15.0",
		"express": "4.15.2",
		"pg": "6.1.5"
	},
		"repository": {},
		"engines": {
		"node": "6.9.4"
	}
}
```

Create a folder "public" and add the index.html



### OPTIONAL
### Install HTTP-REST-Project-Generator package

  sudo npm install -g express-generator

### Install HTTP-REST-Project-Generator package

  sudo npm install -g nodemon

### Tests

  npm install -g mocha
  
  
### How to use

  nodemon bin/www
  
### Questions

1. How to add more dependencies?
2. How to setup and use tests?
3. Setup IDE?
4. How to run tests on push?
  
https://nodejs.org/en/

https://www.npmjs.com/

https://www.npmjs.com/package/express

https://www.npmjs.com/package/express-generator

https://www.npmjs.com/package/nodemon
