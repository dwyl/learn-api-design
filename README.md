UPTIME -> https://www.reddit.com/r/devops/comments/vi1nx5/which_tool_to_use_for_monitoring_uptime_of_apis/



<div align="center">

# Learn API Design

Essential learning for people building an API
that is performant, scalable and maintainable.

[![HitCount](https://hits.dwyl.com/dwyl/learn-api-design.svg?style=flat-square&show=unique)](http://hits.dwyl.com/dwyl/learn-api-design)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/dwyl/learn-api-design/issues)

</div>

![Grandma Remote](https://i.imgur.com/pdrRPjm.jpg)

Joking aside, ***starting*** a project "***from scratch***" is a ***opportunity***
(and *privilege*) ***few people get***.  
If you are ***fortunate*** enough to be
in that position, ***do not take*** the **task** ***lightly***.

![golden ticket](https://i.imgur.com/U6a5SCh.jpg)

Building the *interface* for a new project is nothing short of a ***Golden Ticket***! So do your homework *before* you start!

## Intro

Having a *great* API will make or break your project/product.

A few ***quotes*** from
[**Joshua Bloch**](http://en.wikipedia.org/wiki/Joshua_Bloch)'s
Google Talk on
["***How To Design A Good API and Why it Matters***"](http://youtu.be/heh4OeB9A-c)  
and [Kevin Lacker](https://twitter.com/lacker)'s ([@Parse](http://parseplatform.org/))
["***How to Design Great APIs***"](https://www.youtube.com/watch?v=qCdpTji8nxo)
> - - -
> "*You have* ***one chance*** *to* ***get it right***."
[3:17](http://youtu.be/heh4OeB9A-c?t=3m17s)
- - -
> "***A bad API*** *can be among a company's greatest liabilities...*
> *can cause an un-ending stream of support phonecalls ...*
*and it* ***can inhibit*** *a company's* ***ability to move forward***"
[2:51](http://youtu.be/heh4OeB9A-c?t=2m51s)
- - -
> "*Once you have a* ***bad API***, *you* ***can't change it***,
*you are pretty much* ***stuck with it forever***." [3:12](http://youtu.be/heh4OeB9A-c?t=2m51s)
- - -
> " ... ***A good API*** *needs to* ***appeal to*** *the most powerful emotion*: ***Laziness***".
[3:23](http://youtu.be/qCdpTji8nxo?t=3m23s)
- - -
> "*You need to* ***be opinionated*** *even when* ***there is no right and wrong***"
[31:02](http://youtu.be/qCdpTji8nxo?t=31m2s)
- - -
> "*Always make your REST API* ***as small/short as possible***"
[31:19](http://youtu.be/hdSrT4yjS1g?t=31m19s)
- - -
> "The user of an API **should never be surprised by its behaviour**... it's even sometimes worth reduced performance *not to surprise users of the API*."
[48:32](http://youtu.be/hdSrT4yjS1g?t=48m32s)
- - -

## Characteristics of a Good API

+ ***Easy to learn*** (*notice the priority placement of learn-ability...*)
+ Intuitive / Easy to ***use*** even without documentation
+ ***Hard to misuse*** (*write tests for "undesirable" behaviour*)
+ Easy to *read* and *maintain* code that uses it
+ Sufficiently powerful to satisfy requirements
+ Easy to ***evolve*** (*the simpler the initial API the easier it will be to extend*)
+ Appropriate to ***audience*** (*make it beginner friendly*...)
+ ***Opinionated*** (means people don't have to *think*)

## But wait... what is an API, after all?

The term `API` itself is quite generic and in layman's terms, 
an API is just a **way of communicating with an interface programmatically**.
It is a structured way for one program to offer services to other programs.

Let's take the example of the 
[`Twitter API`](https://developer.twitter.com/en/docs/platform-overview).
We could use it to write a bot that displays the top tweets of the day.
We, as users, don't need to know about the internal details
of Twitter's systems, 
nor does Twitter want us to.
But using their API, we  are able to do specific things
(like making a post or reading a timeline).
**Twitter is exposing us features through an interface
that we can consume**.

If you've been around the web,
you might have noticed that most of these APIs
served by big companies like [`Google`](https://cloud.google.com/apis/docs/overview)
or [`Microsoft`](https://developer.microsoft.com/en-us/graph)
are often referred to as `REST API`s.

Let's figure out what this is! 😉


## Types of API

An API comes in different forms.
When a developer get down to building an API,
they first decide which specification to use.
Most of the time, they go for `REST`.
But, analysing product requirements, 
a tech team may come to the conclusion 
that calls for a different approach.

`RESTful` APIs weren't always the *de facto* way of building APIs.
In fact, there is an historical precedence to it.

### RPC

The earliest and simplest form of API
was **`RPC` Remote Procedure Call**,
hailing from the 80's.
The name speaks for itself.
It's a straightforward interaction where a local client
sends commands to a remote server.

Here's a closer look at how it works.
Both client and server use different call params,
so they must be converted so it is understood by the other side.
This conversion is made inside **stubs**.

<img width="1418" alt="workflow RPC" src="https://user-images.githubusercontent.com/17494745/209990909-d2996bea-3162-4915-941d-944773505be4.png">

`RPC` started with `XML` and later `JSON`-based versions.
However, in 2015, Google created [`gRPC`](https://grpc.io/),
a general-purpose `RPC` framework.
Systems like Facebok's [`Apache Thrift`](https://thrift.apache.org/)
or Twitch's [`Twirp`](https://blog.twitch.tv/en/2018/01/16/twirp-a-sweet-new-rpc-framework-for-go-5f2febbf35f/)
use `gRPC` for internal communication between microservices.

In these services, as *millions* of calls are made per-day,
it takes a **really** performant API to optimize the network layer,
and `RPC` style is suitable for these scenarios,
because of its short and lightweight messages, 
it *goes easy on the network*, making it fast 💨.

### SOAP 

In 1999, a year after `RPC` was created it,
Microsoft scrubbed it away with [`SOAP`](https://en.wikipedia.org/wiki/SOAP) - 
**Simple Object Access Protocol**.

Initially, `XML` `RPC` had a problem - 
it didn't distinguish between data types.
So devs had to add additional metadata to label a field with a data type.
Aiming for consistency, 
`SOAP` carved the format of the transmitted message *in stone*.
It was informative but *rather verbose*.

<img width="1413" alt="soap" src="https://user-images.githubusercontent.com/17494745/209992355-6bb307a5-52fb-47c7-8718-edd6811c3621.png">


A `SOAP` message **is framed with an envelope tag** 
(root element that starts and ends the message),
**a header** and **a body**.

Although `SOAP` is not as popular as `REST`,
it's still around, especially in financial services.
This is because it is **secure** 
([`WS-Security`](https://en.wikipedia.org/wiki/WS-Security)).
`SOAP WS-Security extension` encrypts a message 
and only the recipient with a security token can read it.

### REST

**Representational State Transfer** (**REST**) is a software architecture
style consisting of guidelines and best practices for creating
scalable web services.
This is an architectural pattern
that describes how systems
can expose a consistent interface.
When people use the term `REST API`, 
they are referring to an API accessed via `HTTP` protocol
at a predefined set of URLs.

Whilst `SOAP` allows for stateful interactions 
(where the server is aware of previous requests),
`RESTful` APIs are **stateless**, 
thus treating every request as new.

`RESTful` APIs are **resource-based**, 
meaning the user is manipulating 
(creating, updating, deleting or fetching) resources.
You can see an example of this
with Microsoft's [`Graph Explorer API`](https://developer.microsoft.com/en-us/graph/graph-explorer).

<img width="1214" alt="graphAPI" src="https://user-images.githubusercontent.com/17494745/209994353-a2c94374-720b-4b7e-b4e7-aa1409f71165.png">

We are accessing the **URI - Uniform Resource Identifier**
and doing **an action** - a `GET` (fetching) request.
with an `HTTP` request.
The response is a `JSON` with the profile of the user.


#### What is a RESTful web service?

![restful API](https://i.imgur.com/xKXnKGT.jpg)

[REST](http://en.wikipedia.org/wiki/Representational_state_transfer)
is a structured way of building web services and applications.
When something is described as "RESTful" it simply means it follows a
predefined predictable pattern for how it responds to requests.

For a system to be considered 100% `RESTful`, 
it **must** follow six constraints:
- [Uniform Interface](https://stackoverflow.com/questions/25172600/rest-what-exactly-is-meant-by-uniform-interface)
- [Statelessness](https://en.wikipedia.org/wiki/Stateless_protocol)
- [Client-server](https://en.wikipedia.org/wiki/Client%E2%80%93server_model)
- [Cacheable](https://en.wikipedia.org/wiki/Web_cache)
- [Layered System](https://en.wikipedia.org/wiki/Layered_system)
- [Code-on-demand](https://en.wikipedia.org/wiki/Client-side_scripting)

While the **uniform interface** constraint is fundamental
to the design of any `RESTful` system,
**code-on-demand** is optional.
Although not mandatory to implement all of the aforementioned,
doing so will result in better,
more usable services.

We recommend the following videos
for an "easy-to-digest" introduction
to these concepts an `REST` as a whole.

- Intro to REST: http://youtu.be/llpr5924N7E
- What is REST API?: https://youtu.be/-mN3VyJuCjM
- RESTful APIs in 100 seconds: https://youtu.be/-MTSQjw5DrM
- `Google Cloud Tech` Youtube channel for API management, design patterns and summit talks of APIs on the cloud: https://www.youtube.com/channel/UCJS9pqu9BzkAMNTmzNMNhvg

For `web RESTful services`-specific resources,
we encourage you to skim through the following resources.

- Beginners Guide: http://www.restapitutorial.com/
- What are RESTful web services: http://stackoverflow.com/a/3636470/1148249
- What is "CRUD"? http://en.wikipedia.org/wiki/Create,_read,_update_and_delete

#### Using HTTP Methods for `RESTful` Services

[HTTP verbs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
represent one of the pillars of the
**uniform interface** constraint we have mentioned earlier.
Resources are manipulated (CRUD) 
and each operation is invoked by these verbs.

+ **GET** = **read** an existing **record** or collection (list of records)
+ **POST** = **create** and ***partial*** update.
+ **PUT** = **create** and [***idempotent***](http://stackoverflow.com/a/1077489/1148249) update
(always send **all** the fields required - not partial update)
+ **PATCH** = partial update (send only the fields to update)
+ **DELETE** = does exactly what it says

> The word "**idempotence**" may be funky
but it represents a rather simple concept.
For a RESTful service standpoint,
for an operation to be *idempotent*,
clients can make the same call repeatedly while producing the same result.
>
> The `GET` or `PUT` operation on a `users/12345` URI,
for example, are great examples of this.
Each time they are called, the same result is yielded.

Each operation concerns to a *resource*,
which in turn is identified/located 
through an *URI*.
Here's how these operations are applied to resources.

+ **GET** /comment - Returns a list of all comments
+ **GET** /comment/:id - Returns a comment with the given id
+ **POST** /comment - Creates a new comment
+ **PUT** /comment/:id - Updates a comment with the given id
+ **PATCH** /comment/:id - Partially update a comment with the given id
+ **DELETE** /comment/:id - Deletes a comment with the given id

This is an overview of how these are implemented.
If you are curious or want to learn more
about the differences between `PUT`, `POST` and `PATCH`,
skim through the following links for a better understanding.

+ PUT vs POST in REST:
http://stackoverflow.com/questions/630453/put-vs-post-in-rest
+ PUT vs PATCH in REST:
https://stackoverflow.com/questions/28459418/rest-api-put-vs-patch-with-real-life-examples

### Examples of Successful (Good) `RESTful` APIs

You can find endless public APIs across the world-wide-web.
Some of them don't have documentation,
others have decent
and there are others with exceptional 
and comprehensive guides.

Here is a list of examples of public `RESTful` APIs
that have *awesome* documentation.

+ Parse REST API: http://docs.parseplatform.org/rest/guide/
(really good example of good interactive documentation)
+ GitHub: https://developer.github.com/
+ Twitter: https://developer.twitter.com/en/docs
+ Google: https://developers.google.com/custom-search/v1/using_rest
+ Stripe: https://stripe.com/docs/api
+ Twilio: https://www.twilio.com/docs/usage/api


### Realtime APIs

The APIs above are `RESTful`, thus representing resource-based APIs.
As you know, these work over the `HTTP` protocol, which is stateless.
This is ideal for application that need to perform actions on resources
and are request-driven.
This is most adequate for most web apps, cloud apps and microservices
we see everyday.

*However*, these are not particularly good nor performant
when we are looking at **realtime scenarios** - for example, 
a live score sports app.
Since `REST` APIs use `HTTP`, there is bigger overhead per message,
leading to increased latency and higher CPU usage.

**Realtime APIs** exist but they don't use the `HTTP` protocol.
*They use *websockets**.

#### WebSockets

A [**WebSocket**](https://ably.com/topic/websockets)
is a realtime protocol that enables bidirectional communication
between a web client and a webserver
over a single-socket connection.

Similarly to `HTTP`, `WebSocket` works on top of the TCP, 
in the *application layer*. 
However, unlike HTTP, *they are stateful*,
which makes them highly suitable for 
event-driven services that require **high-frequency communication**. 

> If you don't know what a `socket` is,
or if `TCP` is foreign to you,
we recommend you getting familiar 
with [`TCP/IP``, also known as **Internet Protocol Suite**](https://en.wikipedia.org/wiki/Internet_protocol_suite).
![tcp/ip](https://cdn.kastatic.org/ka-perseus-images/6a0cd3a5b7e709c2f637c959ba98705ad21e4e3c.svg)

To create an `WebSocket` connection,
an initial HTTP *handshake* is made,
and then establishes a persistent connection
where both parties exchange data.
Therefore, a `WebSocket` uses *a single TCP connection for data exchange*,
while `RESTful` APIs require a *new TCP connection* 
on every request/response.

![websockets](https://images.ctfassets.net/ee3ypdtck0rk/0mExYcxsnzccWxnktAKjc/d6bacce5d564f04c7128a3b6cd52e877/websockets.png?w=745&h=724&q=50&fm=webp)

If you want to learn more
about WebSockets,
you should visit our [`learn-websockets`](https://github.com/dwyl/learn-websockets)
repo for a more comprehensive introduction.

Additionally, here are some useful resources
if you want to expand knowledge about this topic.

+ **Q**: Can we use WebSockets? http://caniuse.com/#feat=websockets  
**Answer**: ***YES***! IE 10+, Safari/iOS Safari 7.1+, Android 4.4+ & Android Chrome
+ WebSockets in 100 seconds: https://youtu.be/1BfCnjr_Vjg
+ WebSocket MDN: https://developer.mozilla.org/en/docs/WebSockets
+ W3C WebSocket API: http://www.w3.org/TR/2011/WD-websockets-20110419/
+ CloudFlare WebSockets (good intro): https://developers.cloudflare.com/workers/learning/using-websockets/
+ SitePoint article on WebSockets in HTML5:
http://www.sitepoint.com/introduction-to-the-html5-websockets-api/
+ Socket.io Chat Example (uses express): http://socket.io/get-started/chat/
+ Socket.io Max Connections? 250k:
http://stackoverflow.com/questions/10161796/how-many-users-nodejs-socket-io-can-support


#### Examples of Realtime APIs

One of the biggest usages of realtime APIs
is in the financing world - 
specifically stock/options/crypto trading.

[`Polygon.io`](https://polygon.io/)
is one of the most widely used APIs 
for stock market data visualization.

They offer a `RESTful` API 
but also [provide a **`WebSocket API`**](https://polygon.io/docs/stocks/ws_getting-started),
where the user connects to a 
*WebSocket URI* (e.g. `wss://socket.polygon.io/stocks`)
and receives data as the stock prices change overtime.

There are other examples worth mentioning:
+ Twitter Streaming API:
https://dev.twitter.com/streaming/overview
+ Salesforce Streaming API:
http://www.salesforce.com/developer/docs/api_streaming/
+ Google Real Time Reporting API: https://developers.google.com/analytics/devguides/reporting/realtime/v3

----------------

## `RESTful` API Design and Best Practices

DESIGN GUIDE
https://www.restapitutorial.com/lessons/restquicktips.html
https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design
https://www.freecodecamp.org/news/rest-api-design-best-practices-build-a-rest-api/
https://cloud.google.com/apis/design




## links
+ Best Practices for Designing a Pragmatic RESTful API (***Great*** article)
http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
+ REST+JSON API Design - Best Practices for Developers
http://youtu.be/hdSrT4yjS1g (*comprehensive* overview)
+ Secure Your API - Tips for REST + JSON Developers
http://youtu.be/FeSdFhsKGG0




#### Tips

To reduce the amount of data retrieved,
we can *specify* the exact fields we want in url e.g:
```
GET /accounts/1234/fields=firstname,surname,etc
```
see: [52:29](http://youtu.be/hdSrT4yjS1g?t=52m29s)



## Versioning your API?

![API Versioning](http://i.imgur.com/lu5DhRy.jpg)

There is on-going debate on whether APIs should be versioned
and if so, how should this be done.

There are two primary approaches to versioning [32:43](http://youtu.be/hdSrT4yjS1g?t=32m43s)

### Intro Reading

+ Your API versioning is wrong:
http://www.troyhunt.com/2014/02/your-api-versioning-is-wrong-which-is.html
+ The debate on API versioning:
http://stackoverflow.com/questions/389169/best-practices-for-api-versioning
+ Issues with API version in the URL/URI:
https://www.mnot.net/blog/2012/12/04/api-evolution
+ Evolving HTTP APIs
https://www.mnot.net/blog/2012/12/04/api-evolution

### Wrong way 1 – URL versioning
```sh
HTTP GET:
https://haveibeenpwned.com/api/v2/breachedaccount/foo
```

### Wrong way 2 - custom request header
```sh
HTTP GET:
https://haveibeenpwned.com/api/breachedaccount/foo
api-version: 2
```

### Wrong way 3 - content type
```sh
HTTP GET:
https://haveibeenpwned.com/api/breachedaccount/foo
Accept: application/vnd.haveibeenpwned.v2+json
```
### Further Reading (Versioning)

+ Pivotal Labs API Versioning guide: https://content.pivotal.io/blog/api-versioning
+ SemVer: http://semver.org/
+ Stripe's API Versioning: https://stripe.com/docs/api#versioning
+ *Comprehensive* List of how others are doing versioning:
http://www.lexicalscope.com/blog/2012/03/12/how-are-rest-apis-versioned/

## Caching

+ Caching API Requests:
http://robots.thoughtbot.com/caching-api-requests
+ Caching your REST API
http://restcookbook.com/Basics/caching/
+ API Caching
http://www.fastly.com/blog/api-caching-part-1/
+ Caching and rate limiting:
https://blog.apigee.com/detail/api_scalability_part_2_-_caching_rate_limits_and_offloading
+ Thoughtbot caching insights (mostly ruby-focussed):
http://robots.thoughtbot.com/caching-api-requests


#### Documentation/specification


+ RESTful web API Documentation Generator.
http://apidocjs.com
+ Swagger - The World's Most Popular Framework for APIs:
http://swagger.io
+ Open Source API Management Platform
https://www.fusio-project.org
+ Collection of Public APIs
https://github.com/toddmotto/public-apis

## General Background Reading + Watching

+ What is an API? (very basic intro): http://youtu.be/B9vPoCOP7oY
+ **BASIC** Introduction to APIs by [Derek Dahmer](https://github.com/ddgromit)
@ General Assembly:  
https://www.youtube.com/watch?v=FknvOGcLHmc (Google for Entrepreneurs - *absolute beginner*?)
+ Wikipedia: http://en.wikipedia.org/wiki/Application_programming_interface
+ The REST Cookbook: http://restcookbook.com (comprehensive guide)
+ How to Design Great APIs - Parse:
https://www.youtube.com/watch?v=qCdpTji8nxo
+ How To Design A Good API and ***Why it Matters***:
http://youtu.be/heh4OeB9A-c + http://lcsd05.cs.tamu.edu/slides/keynote.pdf
(mostly related to the Java Language API but a few general insights)
+ Best practices (mostly relating to library APIs not REST/Stream):
http://stackoverflow.com/questions/2619854/best-practices-and-guidelines-for-designing-an-api
+ Parse ***interactive*** API reference:
http://youtu.be/qCdpTji8nxo?t=21m15s
+ Principals of good RESTful API design:
http://codeplanet.io/principles-good-restful-api-design/
+ Building Hypermedia APIs with HTML5 and Node:
http://www.amazon.com/Building-Hypermedia-APIs-HTML5-Node/dp/1449306578
+ Designing APIs for Asynchrony:
http://blog.izs.me/post/59142742143/designing-apis-for-asynchrony
+ API Design Principles: http://qt-project.org/wiki/API-Design-Principles
(general principals. ignore the QT-specific parts)
+ Build an API under 30 lines of code with Python and Flask: https://impythonist.wordpress.com/2015/07/12/build-an-api-under-30-lines-of-code-with-python-and-flask/
+ REST API Tutorial:
http://www.restapitutorial.com/
+ API Design Guidelines:
http://apistylebook.com/design/guidelines/
+ Public Vs Private APIs:
https://www.upwork.com/hiring/development/public-apis-vs-private-apis-whats-the-difference/
+ Learn to work with APIs: https://workwithapis.com
