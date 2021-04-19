## EJS
---

[EJS](ejs.co)

1. What is EJS?
    - Embedded JavaScript templating
    - Allows us to use Templating, so we don't need to create repetitive code, like similiar pages.

2. After Installing and Configuring EJS you can pass variables using the <%= %> tags. 

3. Using the res.render method we can pass over the name of the ejs page and an OBJECT with a key/value pair. | {kindOfDay: day}

4. Wrap all your JavaScript you use from your view file list.ejs with scriptlets so it can render | <% %>

5. Remember to try and keep your LOGIC on the server side and CONTENT on the client side or views.






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
var currentDay = today.getDay();
    var day = ""; 
    switch (currentDay) {
        case 0:
            day = "Sunday"
            break;
        case 0:
            day = "Monday"
            break;
        case 0:
            day = "Tuesday"
            break;
        case 0:
            day = "Wednesday"
            break;
        case 0:
            day = "Thursday"
            break;
        case 0:
            day = "Friday"
            break;
        case 0:
            day = "Saturday"
            break;
    
        default:
            break;
    }
```

```
<body>
    <h1>It's a <%= kindOfDay %>!</h1>
</body>
```

## Scriptlets
---

What are scriptlets?
    - If you go to the EJS documentation you will see their are different tags for ejs that let you do different things.

Control Flow Scriptlets
    - One common sciptlet is the <% %> lets you add if/else statements so now your html can render javascript.

How to add?
    - Wrap every line of code that is JAVASCRPT with your scriptlets for it to render

list.ejs Example Code of wrapping your JavaScript

```
<body>
    <%  if (kindOfDay === "Saturday" || kindOfDay === "Sunday"){ %>
        <h1 style="color: aqua"><%= kindOfDay %> ToDo List</h1>
   <% } else { %>
        <h1 style="color: brown">It's a <%= kindOfDay %>!</h1>
  <%  } %>
    
</body>

```



### EJS Part 2
---

1. Lets shorten our switch statement using javascript formatting to keep it shorter.

```

    var today = new Date();
    var options = {
        weekday: "long",
        day: "numeric",
        month: "long"
    };

    var day = today.toLocaleDateString("en-US", options)


    <h1><%= kindOfDay %></h1>

```


### EJS FORM CHALLENGE
---

1. Lets add a form to our list.ejs

```
  <form action="/" method="post">
        <input type="text" name="newItem">
        <button type="submit" name="button">Add</button>
    </form>
```

2. Console log the text that the user enters into the form when they hit submit.

- Make sure you configured body-Parser.
```
 const bodyParser = require("body-parser");
```


3. Lets create a list on our list.ejs page that loops through our newItemsList. Don't forget to wrap your javascript in EJS.


### Scope
---


What is Scope?
    - Scope is the range in which a variable can be accessed. 
    - You cannot access variable outside the scope in which they were created.
    - Creating Variables outside a function makes it accessible globally.

Differences between the types of variables and how their scope can be accessed.

-Variable inside a function are local variables.
-Variables outside a function are global variables.
-Variables in an if/else/for/do/while: var is global let/const is local

This is why we try to avoid using var, and use let or const instead.


### Adding Local Stylesheets
---

We no longer run a static website, so we need to serve them from the server. Thats why our CSS folder won't work. 
 - This needs to setup for every folder added to the application


Public Folder is our solution. If we add 

```
app.use(express.static("public"));
```

Now we can add our public files/folders into a directory that can be accessed publicy. Don't forget to not put sensitive data in this folder.

### Adding Work List Module
---

1. Create workItems array; Empty;

2. Create get route; res.render our list, passing our new object with listTitle and newListItems

3. Create post route; tap into req.body.newItem entered.

4. Push item to workItems array and res.redirect to work route.



### Layouts and Partials
---

Layouts let you create reusable chuncks of code, that makes consistency and repitition a breeze
    - Think header, footer, multiple page content that we don't want to recode.

1. Create header and footer files.


### Node.js - How to Import and Export Modules
---
[NodeJs-Modules](https://nodejs.org/api/modules.html)

1. Why would we want to import or export a module?
    - This keeps code that doesn't really relate to the application in a seperate area.
    - For example, getDate() preferences

## Import/Export Challenge
---

1. Create date.js, move the code over

2. Create a const called date and require our js file from step1. You will need the --dirname + as this is a local file.
    -const date = require(__dirname + "/date.js");

3. This requires the code to be ran upon load but keep it seperate

4. Lets export the date.js file next
    -  module.exports = "Hello World";  // You can actually export strings
    -  module.exports = getDate;  // No () because we don't want it to run immediately

5. Now that date.js module has been imported/exported we can call it and use it in our main code with cluttering up the application with the unneccesary logic.

6. Now if we want to add another function from the same module we can be more specific when we are exporting
    -  module.exports.getDay = getDay;

7. Refactoring the Date and App js
    - We changed var/let to const
    - removed module.exports and jsut made it exports // as per documentation.
    -  export our anonymous functions all in the same line