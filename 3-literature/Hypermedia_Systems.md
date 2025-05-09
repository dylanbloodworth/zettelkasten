https://hypermedia.systems

# Introduction
## What is a Hypermedia System

A system that follows the REpresentational State Transfer (REST) developed by Roy Fielding.
	**What is REST, really?**

## Goals of the Books
1. Outline differences between Hypermedia Driven Applications (HDAs) and the currently popular single-page applications (SPAs)
2. Strengths and weakness of HDAs
3. Provide the information to answer the question, "*Can I build this as a Hypermedia Driven Application?*"


# Hypermedia: A Reintroduction

## What is Hypermedia?
It's media that included non-linear branching from different locations within that media. These are hypermedia controls

> A hypermedia control is an element in a hypermedia that describes (or controls) some sort of interaction, often with a remote server, by encoding information about that interaction directly and completely within itself.


Hypermedia system ecosystem 
→ HTTP (network protocol transferring hypermedia between client and server)
→ Hypertext (HTML or HXML)
→ Hypermedia servers (include the relevant APIs)
→ Hypermedia clients (web browsers)
→ Images and Videos

## The Essence of HTML as a Hypermedia

The two defining hypermedia controls:

**Anchor**
Provide hyperlinks by specifying a hypertext reference (href) that points to another pieces of the current or other documents.

```
<a href="https://hypermedia.systems/">
	Hypermedia Systems
</a>
```

This tag shows clickable words and issues an *HTTP GET request* for the hypertext reference when clicked. If successful, the HTML in the GET request is used to replace the browser with the new HTML document. The GET request is answered by a *hypermedia server* with a *hypermedia response.*

**KEY FOR RESTful HYPERMEDIA SYSTEMS**: clients and servers must communicate via hypermedia.


**Forms**
```
<form action="/signup" method="post">
  <input type="text" name="email" placeholder="Enter Email To Sign Up">
  <button>Sign Up</button>
</form>
```

Forms allow the client to update the hypermedia resources. There's an *action* tag where to issue HTTP requests and the *method* tag to specify which request to send.


## Hypermedia-Driven Applications

>Hypermedia-Driven Application (HDA): A web application that uses hypermedia and hypermedia exchanges as its primary mechanism for communicating with a server

For these HDAs, it's expected that the response from servers are the HTML format, not something else (like JSON for example).

HTMX is a hypermedia focused library that aims to augment the hypermedia functionality of HTML 


## When to use Hypermedia?

1. When there isn't much user interactivity (things that are mainly text and images, the way the web gods intended)
2. The value of the server-side is more than the client-side

## When to not use Hypermedia?

Shouldn't really use hypermedia systems on the parts of applications that heavily involved dynamic user interfaces.



# Components of a Hypermedia System

## 1. Hypermedia
Media that allows for communication between client and server in a dynamic, nonlinear way (i.e. HTML or HXML)

The HTML hypermedia controls anchor and forms specify targets with *Uniform Resource Locators (URLs)*

> A uniform resource locator is a textual string that refers to, or _points to_ a location on a network where a _resource_ can be retrieved from, as well as the mechanism by which the resource can be retrieved.

URLs contain the protocol being used to communicate between client and server, the domain name of the server, and the path to the resource being targeted

## 2. Protocols
Communication used to transfer hypermedia between the clients and servers.

**Example HTTP 1.1 GET request**
```
GET /book/contents/ HTTP/1.1
Accept: text/html,*/*
Host: hypermedia.systems
```
Contains:
1. The type of request (GET)
2. The path to the resource
3. Protocol version
4. Request Headers (metadata specifying how the server should respond)
	1. Accept
	2. Host

**Example HTTP 1.1 response**
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 870
Server: Werkzeug/2.0.2 Python/3.8.10
Date: Sat, 23 Apr 2022 18:27:55 GMT

<html lang="en">
<body>
  <header>
    <h1>HYPERMEDIA SYSTEMS</h1>
  </header>
  ...
</body>
</html>
```
Contains:
1. Version
2. Response code (200)
3. Response Headers (metadata to help the client display the resource correctly)
4. HTML content

### HTTP Methods
POST → Creates a resource 
GET → Reads a resource
PUT/PATCH → Updates a resource
DELETE → Deleting a resource

Follows the *CRUD* (Create/Read/Update/Delete) pattern.

FUN FACT: In plain HTML, the hypermedia controls (anchor and form) can only issue GET and POST requests. Implementing any other method resorts in having to use JavaScript.

### Response Codes and Caching
They're discussed, but reading about them seems more useful during the hands-on learning process.

## 3. Hypermedia Servers
Any server that can respond with an HTTP response after being hit with an HTTP request.

*Since Hypermedia-Driven Applications don't have much JavaScript on the client-side, developers are not pressured into picking a programming language to create the backend for hypermedia servers.*

## 4. Hypermedia Clients
Typically, web browsers


# REST 
*should revist*
