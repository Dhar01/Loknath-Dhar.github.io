---
title: "Web Fundamentals walk-through [TryHackMe]"
date: 2020-10-10T01:34:53+06:00
tags: ["walkthrough"]
draft: false
---
# Task 2


A **DNS request** is made. When browser knows the server's IP address, it ask the server for the web page which is done with a **HTTP GET** request.

**GET** is an example of a HTTP verb, which are the different types of request. The server responds to the GET request with the web page content. IF the web page is loading extra resources, like *JavaScript*, *images*, or *CSS* files, those will be retrieved in <mark>separate GET requests.</mark>

For most websites now, these request will use **HTTPS**, a secure (*encrypted*) version of *HTTP*. This uses **TLS 1.3** (*normally*) encryption in order to communicate without:
- other parties being able to read the data.
- other parties being able to modify the data.

A **web server** is a software that receives and responds to HTTP(S) requests.
Example: **Apache**, **Nginx**, **Microsoft's IIS**.

HTTP runs on port 80 and HTTPS runs on port 443.

* What request verb is used to retrieve page content?

**Ans**: GET.

* What port do web servers normally listen on?

**Ans**: 80.

* What's responsible for making websites look fancy?

**Ans**: CSS.


# Task 3


#### Requests

There are 9 different HTTP "verbs", also known as methods. Each one has a different function.

**POST** requests are used to send data to a web server.

A HTTP request can be broken down into parts.
```http
GET /index.html
```

The next section is **headers**, which give the server more information about requests.

Finally, body of the requests. For POST requests, this is the content that's sent to the server.

#### Responses

The server reply with a response, a status. Normally it'll be a code. A basic breakdown of the status code is:
1. **100-199** : information.
2. **200-299** : Successes. (*200 OK is the "normal" response for a GET*)
3. **300-399** : Redirects (*the information you want is elsewhere*)
4. **400-499** : Client errors (*client did something wrong, like asking for something that doesn't exist*)
5. **500-599** : server errors (*server tried, but something went wrong on their side*)


* What verb would be used for a login?

**Ans**: POST.

* What verb would be used to see your bank balance once you're logged in?

**Ans**: GET.

* Does the body of a GET request matter? Yea/Nay

**Ans**: Nay.

* What's the status code for "I'm a teapot"?

**Ans**: 418.

* What status code will you get if you need to authenticate to access some content, and you're unauthenticated?

**Ans**: 401.


# Task 4


**Cookies** are small bits of data that are stored in browser.

Each browser store them differently, so cookies won't be able to another browser. They have a huge number of uses, but most common are either **session management** or **advertising** (*tracking cookies*). Cookies are normally sent with every HTTP request made to server.

As HTTP is **stateless** (*each request is independent and no state is tracked internally*), cookies are used to keep track of this. They allow sites to keep track of data.

Cookies have:
1. a **name** : identifies the cookie.
2. a **value** : where data is stored.
3. an **expiry date** : when the browser will get rid of the cookie automatically.
4. a **path** : what requests the cookie will be sent with.

The server is normally what sets cookies, and those come in the response headers (*Set-Cookie*). These can be set from javascript inside browser.

When log in to a web application, normally they given a **Session token**. This allows the web server to identify requests. Stealing someone else's session token can often allow to *impersonate* them.


# Task 5

We can make HTTP reques in many ways, including without browsers. For CTFs, we'll ned to use **cURL** or a programming language as this allows to automate repetitive tasks.

By default, curl will perform GET requests on whatever URL it get suppplied, such as
`curl https://tryhackme.com`

This will retrieve the main page of that website. With command line flags, we can do:
1. The **-X** flag allows to specify <mark>the request type</mark>. Ex: *-X POST*.
2. The **--data** flag allows to specify the data to POST with, which default to plain text data.

#### Time for mini Ctf!

There are some mentioned tasks on the ctf room. By connecting to the server with curl, we can get the flag for answers.

![Screenshot_2020-10-10 TryHackMe Web Fundamentals](https://user-images.githubusercontent.com/25137893/95652510-57c8e580-0b13-11eb-934f-6c21a4a39e25.png)

* What's the GET flag?

**Ans**: thm{162520bec925bd7979e9ae65a725f99f}

![get 01](https://user-images.githubusercontent.com/25137893/95652447-c48fb000-0b12-11eb-82a9-d3969760eb6d.png)

* What's the POST flag?

**Ans**: thm{3517c902e22def9c6e09b99a9040ba09}

![get cookie 02+](https://user-images.githubusercontent.com/25137893/95652443-bb064800-0b12-11eb-85d0-e61057b66bb5.png)

* What's the POST flag?

**Ans**: thm{91b1ac2606f36b935f465558213d7ebd}

![get cookie 03](https://user-images.githubusercontent.com/25137893/95652429-b04bb300-0b12-11eb-88c4-a161de569652.png)

* What's the "Set a cookie" flag?

**Ans**: thm{c10b5cb7546f359d19c747db2d0f47b3}

![set cookie 04](https://user-images.githubusercontent.com/25137893/95652423-a3c75a80-0b12-11eb-96c2-92850974401e.png)

> Note 1: the web site IP address my be differ from deployed machine. That's why I hide it, enter the IP address you get from the room.

> Note 2: I heard this room was *subscirber only*, but at the time of writing, it is completely free.
