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

The `https://` and `/toons` portions aren't part of the domain name --> IP address mapping that we've been talking about.

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


## 3. URIs

### L1 Uniform Resourse Identifiers

> **URI (Uniform Resource Ientifier)**: unique character sequence that identifies a resource that is (almost always) accessed via the internet.

URIs come in two main types:
* URLs
* URNs

### L3 Further Dissecting a URL

There are 8 main parts to a URL, though not all the sections are always present.
Each piece plays a role in helping clients locate the resources they're looking for.

| **Part**    |Required    | Example    |
|--------|---------|---------|
| **Protocol**    |Yes    | http    |  
| **Username**    |No    | waynelagner    |
| **Password**    |No    | pwn3d    |
| **Domain**    |Yes  | jello.app    |
| **Port**    |No (defaults to 80 or 443)   | 8080    |
| **Path**    |No (default to / )    | /boards    |
| **Query**    |No    | sort=createdAt    |
| **Fragment**    |No    | #id    |


### L3 Further Dissecting a URL
The "protocol" (also referred to as the "scheme") is the first component of a URL. It defines the rules by which the data being communicated is displayed, encoded or formatted.

Some examples of different URL protocols:
* http
* ftp
mailto
* https

**Not All Schemes Require a "//"**

The "http" in a URL is always followed by ://. All URLs have the colon, but the // part is only included for schemes that have an authority component.

### L5 URL Ports

The port in a URL is a virtual point where network connections are made.

Ports are managed by a computer's operating system and are numbered from 0 to 65,535 (Though port 0 is reserved for the system API).

Whenever you connect to another computer over a network, you're connecting to a specific port on that computer, which is listened to by a program on that computer. A port can only be used by one program at a time, which is why there are so many possible ports.

The port component of a URL is often not visible when browsing normal sites on the internet, because 99% of the time you're using the default ports for the HTTP and HTTPS schemes: 80 and 443 respectively.

Whenever you aren't using a default port, you need to specify it in the URL. For example, port 8080 is often used by web developers when they're running their server in "test mode" on their own machines.

### L6 URL Paths

On static sites (like blogs or documentation sites) a URL's path mirrors the server's filesystem hierarchy.

For example, if the website https://exampleblog.com had a static web server running in its /home directory, then a request to https://exampleblog.com/site/index.html would probably return the file located at /home/site/index.html.

But technically, this is just a convention. The server could be configured to return any file or data given that path.

**It's Not Always That Simple**

Paths in URLs are essentially just another type of parameter that can be passed to the server when making a request. For dynamic sites and web applications, the path is often used to denote a specific resource or endpoint.

### L7 Query Parameters

Query parameters in a URL are not always present. In the context of websites, query parameters are often used for marketing analytics or for changing a variable on the web page. With website URLs, query parameters rarely change which page you're viewing, though they often will change the page's contents.

That said, query parameters can be used for anything the server chooses to use them for, just like the URL's path.

## 4. Async

### L1 Synchronous vs. Asynchronous

Most of the Python you've written so far is synchronous – each line runs only after the one above finishes.


  ```python
print("I print first")
print("I print second")
print("I print third")
  ```

In **asynchronous (async)** code, long-running operations can pause one task while the program keeps doing something else. Python ships the `asyncio` library for this:

  ```python
import asyncio


async def delay_print(ms: int, text: str) -> None:
    await asyncio.sleep(ms / 1_000)
    print(text)


async def main() -> None:
    print("I print first")
    asyncio.create_task(delay_print(100, "I print third after 100 ms"))
    print("I print second")
    await asyncio.sleep(0.2)  # keep the loop alive briefly


await main()  # Pyodide already has a running event loop
# asyncio.run(main()) - how you'd normally do it
  ```


### L2 Why Do We Want Async Code?

We try to keep most of our code synchronous because it's easier to understand, and therefore often has fewer bugs. However, sometimes we need our code to be asynchronous.

**Example:**  
Whenever you update your user settings on a website, your browser will need to communicate those new settings to the server. The time it takes your HTTP request to physically travel across all the wiring of the internet is usually around 100 milliseconds. 

By making network requests asynchronously, we let the webpage execute other code while waiting for the HTTP response to come back. This keeps the user experience snappy and user-friendly.

As a general rule, we should only use async code when we need to for performance reasons. Synchronous code is simpler.

### L3 Coroutines & the Event Loop

Python's solution to async is the **coroutine**.
 
A coroutine function (declared with `async def`) doesn't run when you call it – it hands you a coroutine object, a task the event loop can schedule later.
While one coroutine is paused (e.g. waiting for I/O, a timer), the loop can give CPU time to something else, so your program never has to freeze.

**Declaring a Coroutine**

Calling dice_roll() returns a coroutine object immediately.

  ```python
import asyncio
import random

async def dice_roll() -> str:
    await asyncio.sleep(1)  # pretend we're waiting on I/O
    if random.random() < 0.5:
        return "success!"
    raise Exception("failure!")
  ```

**Awaiting a Coroutine**

await pauses main() and hands control back to the event loop until dice_roll() completes.

  ```python
async def main() -> None:
    try:
        msg = await dice_roll()  # the event loop runs dice_roll() here
        print(msg)
    except Exception as err:
        print(f"oops: {err}")
  ```


### L4 Why Are Coroutines Useful?

Coroutines are Python's answer to slow I/O. When a coroutine hits a wait – network, disk, database – the event loop can switch to something else, so the rest of your code keeps running.


### L5 Using Coroutines

`await` pauses the current coroutine until the awaited coroutine (or other awaitable) finishes and returns a value. It lets Python switch to other work instead of blocking.

**When to Use Await**

You can only use the await keyword:
* Inside an async def
*  function.
* At top‑level in Pyodide


### L6 Creating Coroutines

While the await keyword is used to wait for a coroutine to complete, the async keyword is used to create a coroutine function. When we call an async function, it returns a coroutine object that can later be awaited.

  ```python
async def get_issue_data(issue_id: str) -> dict[str, str]:
    resp = await pyfetch(f"/api/issues/{issue_id}")
    return await resp.json()


result = await coroutine  # now the coroutine runs and yields the data
  ```



1. async def always returns a coroutine object, even if there's no await inside.

2. The await keyword can only be used inside an async function or at top level in Pyodide.

3. A coroutine doesn't run until you await it or schedule it, e.g. with asyncio.run()






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