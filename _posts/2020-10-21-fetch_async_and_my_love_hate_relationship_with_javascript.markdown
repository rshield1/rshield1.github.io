---
layout: post
title:      "Fetch, Async, & My Love/Hate relationship with Javascript"
date:       2020-10-21 17:32:09 +0000
permalink:  fetch_async_and_my_love_hate_relationship_with_javascript
---


**Let’s talk about Fetch & Javascript.  How does it work?**

Javascript is a funny language. From syntax, hoisting, Async, scopes, etc. It’s not the best at making it easy for developers to understand the way it reads code. I love it at times, but I also hate it.  For starters, JavaScript is a **single-threaded** programming language, which means it can only read code line by line, and run one thing at a time.  Excuse me?

**Now what is fetch?**

Now what is fetch?  Fetch is similar to callback functions. It’s a function that is going to run at a later time. **Fetch** is a built in function in the window object that is also promised based, which means that we can use Async Await, .then() and .catch() More on Async later. 

Lets evaluate my code
```
fetch(`http://localhost:4000/api/v1/games/${gameID}/ratings`, {
            method: 'POST',
            body: JSON.stringify(rating),
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            }
        })
```
I'm making a POST request using fetch.  I want to add a rating to a specific game, then update it in the database.  Fetch takes a url as a parameter and an optional second parameter which you can provide it additional information on the type or request, type of data, and information sent with the request, etc. 

**Ok so what does Fetch do?**

Fetch is used to **GET, POST, PATCH/PUT, or DELETE** API data from an external source (server or database) **asynchronously**, which means that it will branch off from the flow of the code, and create its own flow. It will continue the main program flow, so when you receive the information(response) needed from the API, you will then format the information on the front-end to parse into JavaScript code. You can then update the information on the front-end. Ok that was a mouthful. Just know that **JSON (Javascript object notation)** is used for parsing, storing, and transporting data, normally from a server to/from a webpage.


**Promises **

When you use fetch to obtain information from an external api, you are given a promise. A promise is a commitment to go something. That promise has either 2 results (**resolved**, or **rejected**) with a status code. 

Promises are great when you need to do something that might take a long time in the background, while continuing the flow of your program.  You want to do something with the request after it’s completed, instead of making your program wait for it.

**Then and responses**

Anything in **.then()** will run for a resolved(fulfilled) response.  Fetch will return a response object with information such as headers, status, body, etc.  

```then(response => console.log(response)```

Also the requested information in the body is not accessible from the response object, which means we will now need to chain it with an additional .then(). Before creating the additional .then() we’re using JSON data, so we will need to convert our response to JSON.  This will give us another promise, which when ready, will give us our actual data. 

```then(response => response.json())```

You can also access your data!
```
.then(data => {
        console.log(data))
```

**.catch()** will run for rejected responses. You can use .catch() to either console.log your errors, manipulate the error to return a 404 error page, or create a redirect.  Remember, error handling is used with catch()  data handling is used with then()
```
.catch((error) => {
  console.error('Error:', error);
});
```

**Additional information on utilizing the second parameter** 

You'll need to use the optional second parameter to post/update/delete data to an external API. You’ll need to pass in your method: POST. You’ll also need to pass the information you want to send to the body. Since you can’t send data using JavaScript, You’ll need to covert, the pass it as a JSON object by stringify-ing the body.

Heres how I was able to add a game to my backend api. Disregard dispatch

```
            fetch('http://localhost:4000/api/v1/games', {
                method: 'POST',
                body: JSON.stringify(gameData),
                headers: {
                    'Content-Type': 'application/json',
                    'Accept': 'application/json'
                }
            })
            .then(res => res.json())
            .then(data => console.log(data))
```
1. First let the request know what kind of **method** we want to make.
2. Use **body: JSON.stringify()**. To tell the fetch request that you will be passing JSON.  
3. You’ll also need to add **headers** into your fetch object.


**Async**

The difference between Sync and Async?

**Synchronous code** is read line by line and added to memory. If a function needs to be called, it adds it to the call stack, executes the code in the function, pops out of the call stack, then resumes finishing the code line by line. 

There are some functions that are Async functions like fetch() setTimeout()

**Asynchronous code** means that there will be a delay in executing the code, so we will take this code from the main program flow, then hold this code for you.  This means that we can continue running the rest of our code without waiting. When it is ready, we will put this code in the call stack and continue executing this code when it’s ready. 


I believe that covers the surface, but I will continue to **console.log()** to track the flow of the program. This is great for understanding the complexities of Async in Javascript.

