# Learn HTTP Clients in Python — Notes

**Course:** https://www.boot.dev/courses/learn-http-clients-python

## Contents
1. [Why HTTP?](#1-why-http)
2. [DNS](#2-dns)
3. [URIs](#3-uris)
4. [Async](#4-async)
5. [Headers](#5-headers)
6. [JSON](#6-json)
7. [Methods](#7-methods)
8. [Paths](#8-paths)
9. [HTTPS](#9-https)
10. [Cheat Sheet](#cheat-sheet)
11. [Glossary](#glossary)

---

## 1. Why HTTP?

### L1 Communicating on the Web

**How Does Web Communication Work?**

Two computers need to speak the same language to "communicate".
This language is called a **protocol**.

> **protocol**: system of rules that allows two or more entities of a communications system to transmit information.

The most popular protocol for web communication is **HTTP** (Hypertext Transfer Protocol).

### L2 HTTP Requests and Responses

HTTP is a simple request-response system.

The "requesting" computer, also known as the "**client**", asks another computer for some information.

That computer, "**the server**" sends back a response with the information that was requested.

Example:
Request: "What issues are on Jello?"
Response: ["Fix bug", "Improve auth flow"]

### L3 HTTP Powers Websites

HTTP is a protocol designed to transfer information between computers.

Each time you visit a website, your browser is making an HTTP request to that website's server.

The server responds with all the text, images, and styling information that your browser needs to render its pretty website!

### L4 HTTP URLs

> **URL (Uniform Resource Locator)**: address of another computer, or "server" on the internet

Part of the URL specifies where to reach the server, and part of it tells the server what information we want.

### L5 Using URLs in HTTP

The `http://` at the beginning of a website URL specifies that the http protocol will be used for communication.

Other communication protocols use URLs as well, (hence "Uniform Resource Locator"). That's why we need to be specific when we're making HTTP requests by prefixing the URL with http://.

### L6 Requests and Responses

A "client" is a computer making an HTTP request. Clients send requests and receive responses.

A "server" is a computer responding to an HTTP request. Servers receive requests and send responses

### L7 Pyfetch

> **`pyfetch`**: function designed to work in WebAssembly environments and follows an API pattern similar to the browser's `fetch`API but adapted for Python.

Using Pyfetch

  ```python
responde = await pyfetch(url, method="GET", headers=headers)
response_data = await responde.json()
  ```

* `responde`: data that comes back from the server
* `url`: URL we are making a request to
* `method`: specifies the HTTP methos to use (GET, POST, etc.)
* `headers`: dictionary containing HTTP headers to send with the request
* `await responde.json()`: converts the JSON response data from the server into a Python object

### L8 Web Clients

A client can be any type of device but is often something users physically interact with. For example:

* A desktop computer
* A mobile phone
* A tablet

In a website or web application, we call the user's device the "front-end".
A front-end client makes requests to a back-end server.

### L9 Web Servers

Most websites and apps use a web server to store, sort, and serve data so that it sticks around for longer than a single session, and can be accessed by multiple devices.

**Listening and Serving Data**

A web server serves web resources, such as web pages, images, and other data.

The server is turned on and "listening" for inbound requests constantly so that the second it receives a new request, it can send an appropriate response.

**The Server Is the Back-End**

While the "front-end" of a website or web application is the device the user interacts with, the "back-end" is the server that keeps all the data housed in a central location.

**A Server Is Just a Computer**

"Server" is just the name we give to a computer that is taking on the role of serving data across a network connection.


## 2. DNS

### L1 Web Addresses

In computing, web clients find other computers over the internet using **Internet Protocol (IP) addresses**. Each device connected to the internet has a unique IP address.

**Domain Names and IP Addresses**

When we browse the internet, we type in a human readable domain name.
That domain is converted into an IP address.
The IP address tells our computer where the server is located on the internet.

### L2 Web Addresses Quiz

A domain name is the part of a URL that tells the computer where the server is located on the internet by being converted into a numerical IP address.

An IP address is what your computer is using at a lower level to communicate on a network.

### L3 DNS

A "domain name" or "hostname" is just one portion of a URL.

Example: https://homestarrunner.com/toons has a hostname of homestarrunner.com.

The`https://` and `/toons` portions aren't part of the domain name --> IP address mapping that we've been talking about.

**Parsing a URL in Python**

Python provides the `urlparse` function from the urllib.parse module that helps parse URLs into their components:

  ```python
from urllib.parse import urlparse

parsed_url = urlparse("https://homestarrunner.com/toons")
  ```

And then you can extract just the hostname using the hostname attribute:

  ```python
hostname = parsed_url.hostname
print(hostname)  # homestarrunner.com
  ```


### L4 What is the Domain Name System?

> **DNS (Domain Name System)**: phonebook of the internet. DNS "resolves" domain names to their associated IP addresses so that web clients can find the server they're looking for.

Domain names are for humans, IP addresses are for computers.

**How Does DNS Work?**

ICANN is a not-for-profit organization that manages DNS for the entire internet.

If you think of DNS as a phonebook, ICANN is the publisher that keeps the phonebook in print and available.

Whenever your computer attempts to resolve a domain name, it asks a DNS resolver whose address is included in your computer's networking configuration.

From there, the resolver works its way down from one of ICANN's "root nameservers" to gather the domain records for a specific domain name from the distributed DNS database.

### L5 Subdomains

A subdomain prefixes a domain name, allowing a domain to route network traffic to many different servers and resources.

For example, docs.github.com is a subdomain of github.com. The docs subdomain likely routes to a different server than the main github.com domain.









## 7. Methods

### Lesson 7.1: 

- **Code:**
  ```python

  ```

**Methods comparison:**
| Method | Purpose | Has body? | Idempotent? | Example |
|--------|---------|-----------|-------------|---------|
| GET    |         |           |             |         |
| POST   |         |           |             |         |
| PUT    |         |           |             |         |
| DELETE |         |           |             |         |

---

## 8. Paths

### Lesson 8.1: 

- **Code:**
  ```python

  ```

## 9. HTTPS

### Lesson 9.1: 

- **Code:**
  ```python

  ```
---

## Cheat Sheet
**Status codes**
| Code | Meaning | When I'd see it |
|------|---------|-----------------|
|      |         |                 |

**Common request snippets**
```python
# GET

# POST with JSON

# Custom headers

# Error handling
```

---

## Glossary
| Term | Definition |
|------|------------|
|      |            |

---