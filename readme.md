## EJS
---

1. What is EJS?
    - 






## EJS Project
---    

Getting Started

1. Create Dir
2. Touch index.html and app.js
3. npm init, default settings, yes
4. npm i express 
5. npm i body-parser
6. Setup App.js with template // Listed Below

```
//jshint esversion:6


const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.get("/", function (req, res ){
    res.send("Hello");
})

app.listen(3000, function(){
    console.log("Server started on port 3000");
})

```

7. 