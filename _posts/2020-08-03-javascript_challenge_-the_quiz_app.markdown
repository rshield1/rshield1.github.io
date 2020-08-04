---
layout: post
title:      "Javascript Challenge -The Quiz App!"
date:       2020-08-04 00:02:42 +0000
permalink:  javascript_challenge_-the_quiz_app
---


With everything going on, javascript was a bit of a challenge. I'll dive into the complexities of the syntax, flow, and the frequent updates, but I'll tackle the issues that I primarily experienced beginning with the lessons. From dealing with COVID-19, a sudden cohort shift, beginning a new position at the airport, and having family issues, it seemed like my momentum was slowing down tremendously.  The JS labs were hit or miss, and I had a tough time grasping a few concepts, such as certain ES6 methods (...spread, reduce, set timeout, the arrow function) and also fully understanding serializers.  I knew when project week began, I'd have to really spend 3/4ths of the day coding and researching every component of building my application.  From setting up the div#ids in my html body, Styling it with CSS, and building asynchronous code. Being able to plan out my application was extremely vital to my success.

- Settling on the app idea
- 
 I was able to use draw.io to create a diagram representing my models and their relationships.
I wanted to make something that was fairly simple, but enough to show my proficiency in JavaScript, and creating an API with Rails on the backend.  I was primarily leading with creating a card app, then a fake twitter app, or either a ping-pong game.  I decided to settle with a basic quiz-app.  I could easily save and delete a user using the JSON fetch() function, "then" receive the promises to load my users, questions, and answers from my backend server to manipulate the DOM to append them on the html body.  

After reading the project planning resources, structuring my code didn't seem too difficult, after I decided on my application.  Building vertically helped my flow make sense, helping make the jump from backend to front fairly easy.  It also helped me remember to set up all associated ids and classes.

My models/relationships:

User
Quiz - has many questions
Question - belongs to :quiz, has_many :answers
Answer - belongs to :question

Commonly used methods.

(For in) was used often since I was constructing a collection of objects. I define my object (singular) that comes from my objects (plural), which then I'm able to manipulate each iteration from the objects.

``` function grabUsers() {
                fetch(`${BASE_URL}/users`)
                .then(res => res.json())
                .then(users =>{
                    for (let user of users){
                        let u = new User(user.id, user.username, user.total)
                        u.renderUser();
```

ClassList.add & ClassList.remove
I was able to maniupulate the DOM very well using a classList (".hide") and using remove() when applicable.  I didn't want to necessarily remove most of the content I've created, but if I can create and style the hide class, I can append or remove it from the selected element during an event or action.

Constructors
I used constructors to create objects with certain methods attached to them.  Similar to initialize in rails, a constructor of an object takes in paramaters that will be defined during the initialization phase of the class.  For example:

```class User {
    constructor(id, username, total){
    this.id = id
    this.username = username;
    this.total = total;
    }
		
		``` 
"this" refers to the object it belongs to.  In this case, its referring to the initialized user object within the scope, not the actual window or document.  The best way I've checked my scope was to throw in a debugger, then highlight the "this" keyword in the source tab, and/or open up the console, and type "this."  It will return the current scope "this" belongs to.

Next step was to instantiate or call the method on that particular created object.  In order to initialize this step, I had to create a function within the User object which will become available when I create the User. 
		

```
    renderUser(){
        
        usersDiv.innerHTML +=
        `
        <div id="hud-item-users" "data-id"=${this.id}>
        <h3 id="user-username">${this.username}</h3>
        </div>
        <button class="delete-user" data-id=${this.id} onclick="deleteUser()">Delete User</button>
        `
        hudUser.innerHTML = this.username
    }
}```

Static methods are the complete opposite of instance methods.  Static lets you call a function on the actual object without creating/initializing it.

- Console.log & Debugger
Throughout this entire project, I've made great use of console.log and debugger to solve complex issues I've ran into. Debugger is great, because it allows me to pause at any given point and access either my code and it's variables within the current scope. Console.log helps to see what information is defined in the actual argument and logs it into the console.  In many cases, console.log is just enough to help solve most issues, however debugger is more of an advanced way of pausing your code, and working through each step of your code.

Also, my instructor introduced an efficient use of console.log to track what you're logging.  The function console.log() can take in 2 arguments ("string", variable) This allows you to track your logs with meaningful "strings" that are associated with the variables.  Cool Trick!!


-Extras,  Problems, and things to review


-Going through the requirements
This guide also kept me on track to make sure I am completing all required steps to continue to the assessment.
x README.md
x Object Oriented JavaScript (classes)
x domain model served by the Rails backend must include a resource with at least one has-many relationship
x 3 AJAX calls, covering at least 2 of Create, Read, Update, and Delete (CRUD).
x JavaScript code must use fetch with the appropriate HTTP verb, and your Rails API should use RESTful conventions.
x Use classes and functions
x JSON responses into JavaScript model objects using ES6 class or constructor function syntax
x ES6 features
x Follow Rails MVC and RESTful conventions.
x Aim for a large number of small commits

Now the things I will continue to review until assessment time will be:
- variables
- data structures
- functions
- hoisting
- scope
- context
- this
- closures
- ES6 syntax
- let, const
- arrow functions
- Use render json: to render serialized JSON
- Select, Create, and Modify DOM nodes
- Attach listeners to DOM nodes to respond to user interaction
- Use preventDefault to control form submit behavior
- Use fetch with 'GET', 'POST', 'PATCH' & 'DELETE' HTTP methods
- Create a JavaScript object with ES6 class syntax
- Instantiate JavaScript objects and call methods on them.

More to come soon, but feel free to check out my quiz-app and I welcome feedback!  It took a while, but I feel great about it!!!

