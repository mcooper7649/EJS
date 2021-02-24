## EJS
---

[EJS](ejs.co)

1. What is EJS?
    - Embedded JavaScript templating
    - Allows us to use Templating, so we don't need to create repetitive code, like similiar pages.

2. After Installing and Configuring EJS you can pass variables using the <%= %> tags. 

3. Using the res.render method we can pass over the name of the ejs page and an OBJECT with a key/value pair. | {kindOfDay: day}






## EJS TODO list Project
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

7. Create an if/else statement using new Date() and dates method getDay();  and return a message saying weather its the weekend or not. 
    - 6 being saturday and 0 being sunday (part of the Date Functionality)

8. Start Nodemon so we can interact with the app. | nodemon app.js 

9. Lets Configure our index.html file with boilerplate.

10. Lets add res.sendFile(__dirname + "/index.html") 



### EJS Configuration
---

1. Install EJS | npm i ejs

2. Setup EJS | app.set('view engine', 'ejs')

3. Now that we have EJS install it allows us to use res.render and it can access the views directory, in this case 'index'

4. Lets create the views folder now for our ejs pages

5. Create list.ejs file in the views folder and copy the index.html code.

6. Edit the h1 to leave the day name blank. //<h1>It's a !</h1>

7. Add the res.render and pass name of the views file and the object with the key/value pairs.

8. Now lets edit our page to render for each day of the week usikng what we learning.

```
if (currentDay === 0){
        day = "Sunday";
        res.render("list", {kindOfDay: day})
    } else if (currentDay === 1){
        day = "Monday";
        res.render("list", {kindOfDay: day})
    } else if (currentDay === 2){
        day = "Tuesday";
        res.render("list", {kindOfDay: day})
    } else if (currentDay === 3){
        day = "Wednesday";
        res.render("list", {kindOfDay: day})
    } else if (currentDay === 4){
        day = "Thursday";
        res.render("list", {kindOfDay: day})
    } else if (currentDay === 5){
        day = "Friday";
        res.render("list", {kindOfDay: day})
    } else {
        day = "Saturday";
        res.render("list", {kindOfDay: day})
    }
```

```
<body>
    <h1>It's a <%= kindOfDay %>!</h1>
</body>
```