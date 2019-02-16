---
layout: post
title:      "Javascript - Promises and Asynchronous Calls (e.g. 'Fetch')"
date:       2019-02-16 21:49:27 +0000
permalink:  javascript_-_promises_and_asynchronous_calls_e_g_fetch
---


Javascript is a synchronous and single threaded language. This means that, as a language, Javascript cannot perform another operation until it has finished completing the immediately previous operation / action. In short - in Javascript, one line of code is being executed at a time. With that said, Javascript has certain callback functions that allow software engineers the ability to have Javascript behave asynchronously. One example of such a call back function is fetch(). 

Before diving into further detail about how Javascript uses fetch() to behave asynchronously, I’m going briefly walk through the concept of promises in Javascript. In real life, a promise is when you tell your best friend you are going to do something for them at a later time. In Javascript, a promise represents the eventual result of an asynchronous operation. 

A promise is a Javascript object that will eventually produce a value (or error information) in the future. It allows for an asynchronous function to behave synchronously. A synchronous function blocks an operation from proceeding until it completes while an asynchronous function initiates the operation it is performing and does not block it from proceeding before it completes. Using a promise allows you to call an asynchronous function, but prevent the execution of the remainder of your code until a success or failure results from the asynchronous function call. 

Promises are ‘thenable’ meaning that after the result of the asynchronous function within the promise is resolved, you can add a .then() which allows you to perform another action / call another function on the result of the promise. It is recommended to end all promise chains with a .catch(). The .catch() function will allow you to introduce code to your promise that will fire in the event of an error when calling your asynchronous function.

Fetch() is a function that I’ve used specifically in my React / Redux final project to GET, POST, PUT, or DELETE information from the Rails API I’ve linked my project to. Each time I use fetch, a promise is returned that will ultimately provide a response from the http request I’ve specified (or an error if the http request is unsuccessful). Using a promise in this instance allows me to perform an asynchronous action (initiating the http request), but not execute the remainder of my code until the request has resolved, allowing me to take information from the request and dispatch it to my redux reducer. This pattern allows me to connect my API to my front-end React application and prevents additional code from executing without receiving a data response from the http request (as well as preventing code from executing if there is an error with the request).

