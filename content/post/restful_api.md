---
title: "RESTful API Basic"
categories:
  - "computer"
tags:
  - "RESTful API"

---

REST (RESTful) API — stands for representational state transfer and runs mostly on the programming language JSON. Most public APIs use this because of its fast performance, dependability and ability to scale by reusing modular components without affecting the system as a whole.
<!--more-->

We can communicate with REST APIs using HTTP requests, much like you’d do to navigate to a website or load an image. We can do HTTP requests to certain API urls and these urls would then return the information we required, or we could push data to an API url in order to change some data in a database.

Typically we send HTTP requests to an URL that we have defined in our REST API and it would either perform a given task for us or return a certain bit of data. Most APIs these days would return a response to us in the form of JSON.

![RESTful](https://images.tutorialedge.net/uploads/rest-api.png)

This API gives access to data by using a uniform and predefined set of operations. REST APIs are based on URLs and the HTTP protocol and are based on these 6 architectural constraints:

1. Client-server based — the client handles the front end process while the server handles the backend and can be both replaced independently of each other.

2. Uniform interface — defines the interface between client and server and simplifies the architecture to enable each part to develop separately

3. Stateless — each request from client to server must be independent and contain all of the necessary information so that the server can understand and process it accordingly.

4. Cacheable — maintains cached responses between client and server avoiding any additional processing

5. Layered system — layers are arranged hierarchically so that each one can only ‘see’ the corresponding layer they are interacting with.

6. Code-on-demand — allows client functionality to be extended by downloading and executing code in the form of applets and scripts. This simplifies clients by reducing the number of features required to be pre-implemented.

Once you follow these defined constraints the API you create is said the be RESTful.

A Simple Example

Imagine you wrote a bit of code that gives you the current weather conditions at your house. It reads the temperature, humidity and rainfall and stores them locally. How would we then expose this information in such a way that websites or other applications could view it?

One answer to this question is by wrapping it in a RESTful API.

We could expose our code and wrap it in an API so that whenever we navigated to say `http://localhost:8000/api/weatherStats` it would give us a JSON response that contained all the current weather stats.



