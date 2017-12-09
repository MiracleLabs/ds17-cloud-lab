# Building a Cloud Application on IBM Bluemix(PaaS)

This document will have all the links, code snippets and notes that you will need to complete this lab - Building a Cloud Application on IBM Bluemix(PaaS) Platform.

## Important Links

Access Bluemix - http://bluemix.net
Installing Node JS - https://nodejs.org/en/

## Commands

```
node app.js - Running Node JS application on server

```

## Code Snippets

The following code snippets will help you in creating the final Consumer Application.

### app.js

```
var express = require('express'); //requiring express library
var app = express();
var path = require('path');
var port = process.env.PORT || 3000;
var host = process.env.HOST || 'localhost' ;

//serving static files in express
app.use('/', express.static(path.join(__dirname, 'public')))

//creating a route to serve html file
app.get("/htmlpage",function(req,res){
 res.sendFile(__dirname + "/public/" + "index.html");
});

//creating server
app.listen(port, function(){
 console.log("Server was started on Bluemix with your app @ /htmlpage");
 console.log("Your App is running at "+host+":"+port);
});

```

### index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Theme Made By www.w3schools.com - No Copyright -->
  <title>Bootstrap Theme Simply Me</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
  <link href="https://fonts.googleapis.com/css?family=Montserrat" rel="stylesheet">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
  <style>
  body {
      font: 20px Montserrat, sans-serif;
      line-height: 1.8;
      background-color:black;
  }

  .container-fluid {
    padding-top: 130px;
    padding-bottom: 70px;
}

img{
    vertical-align: middle;
    margin-top: 50px;
}

  </style>
</head>
<body>

<div class="container-fluid bg-3 text-center">    
   <img src="Miracle_White.png" class="img-responsive" style="display:inline" alt="Bird" width="350" height="400"><br><br>
   <h2 style="color:#fff">Hello World Cloud Application Lab</h2>
</div>
</body>
</html>

```
### package.json

```
{
    "name": "nodejs-cloudlab",
    "version": "1.0.0",
    "description": "Pushing NodeJS Application to IBM Bluemix",
    "main": "app.js",
    "dependencies": {
        "express": "^4.13.4"
    },
    "devDependencies": {},
    "scripts": {
        "start": "node app.js"
    },
    "author": "Miracle Labs",
    "license": "ISC"
}

```

### manifest.yml file for deploying to Bluemix

```
applications:
- path: .
  memory: 256M
  instances: 1
  domain: mybluemix.net
  name: nodejs-cloudlab
  host: nodejs-cloudlab
  disk_quota: 1024M

```		
