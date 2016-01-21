# Learn API Design [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/dwyl/learn-api-design/issues)

Essential learning for people building an API

![Grandma Remote](http://i.imgur.com/pdrRPjm.jpg)

Joking aside, ***starting*** a project "***from scratch***" is a ***opportunity***
(and *privilege*) ***few people get***.  
If you are ***fortunate*** enough to be
in that position, ***do not take*** the **task** ***lightly***.

![golden ticket](http://i.imgur.com/U6a5SCh.jpg)

Building the *interface* for a new project is nothing short of a ***Golden Ticket***! So do your homework *before* you start!

## Intro

Having a *great* API will make or break your project/product.

A few ***quotes*** from
[**Joshua Bloch**](http://en.wikipedia.org/wiki/Joshua_Bloch)'s
Google Talk on
["***How To Design A Good API and Why it Matters***"](http://youtu.be/heh4OeB9A-c)  
and [Kevin Lacker](https://twitter.com/lacker)'s ([@Parse](https://parse.com/products))
["***How to Design Great APIs***"](https://www.youtube.com/watch?v=qCdpTji8nxo)
> - - -
> "*You have* ***one chance*** *to* ***get it right***."
[3:17](http://youtu.be/heh4OeB9A-c?t=3m17s)
- - -
> "***A bad API*** *can be amoung a company's greatest liabilities...*
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

## Characteristics of a Good API

+ ***Easy to learn*** (*notice the priority placement of learn-ability...*)
+ Intuitive / Easy to ***use*** even without documentation
+ ***Hard to misuse*** (*write tests for "undesireable" behaviour*)
+ Easy to *read* and *maintain* code that uses it
+ Sufficiently powerful to satisfy requirements
+ Easy to ***evolve*** (*the simpler the initial API the easier it will be to extend*)
+ Appropriate to ***audience*** (*make it beginner friendly*...)
+ ***Opinionated*** (means people don't have to *think*)


## Types of API

### REST

**Representational State Transfer** (**REST**) is a software architecture
style consisting of guidelines and best practices for creating
scalable web services.


### What is a RESTful web service?

![restful API](http://i.imgur.com/xKXnKGT.jpg)

[ReST](http://en.wikipedia.org/wiki/Representational_state_transfer)
is a structured way of building web services and applications.
When something is described as "RESTful" it simply means it follows a
predefined predictable pattern for how it responds to requests.

#### Video Explanation of REST

- Intro to REST: http://youtu.be/llpr5924N7E
- Google Developers Intro to REST: https://www.youtube.com/watch?v=YCcAE2SCQ6k

#### Read more about REST APIs / RESTful Web Services

- REST Wikipedia: http://en.wikipedia.org/wiki/REST (*Skim* and make sure you understand the concepts)
- Beginners Guide: http://www.restapitutorial.com/
- Basic Q&A for REST: http://katgleason.tumblr.com/post/37836552900/how-i-explained-rest-to-my-wife
- What are RESTful web services: http://stackoverflow.com/a/3636470/1148249
- What is "CRUD"? http://en.wikipedia.org/wiki/Create,_read,_update_and_delete


#### Why REST?

+ Scalability (dissemination - more people use your API)
+ Generality
+ Independence
+ Latency (Caching)
+ Security
+ Encapsulation

#### Verbs

+ **GET** = **read** an existing **record** or collection (list of records)
+ **POST** = **create** and ***partial*** update.
+ **PUT** = **create** and [***idempotent***](http://stackoverflow.com/a/1077489/1148249) update
(always send **all** the fields required - not partial update)
+ **DELETE** = does exactly what it says

##### Examples

+ **GET** /comment - Returns a list of all comments
+ **GET** /comment/:id - Returns a comment with the given id
+ **POST** /comment - Creates a new comment
+ **PUT** /comment/:id - Updates a comment with the given id
+ **DELETE** /comment/:id - Deletes a comment with the given id

#### Tips

To reduce the amount of data retrieved,
we can *specify* the exact fields we want in url e.g:
```
GET /accounts/1234/fields=firstname,surname,etc
```
see: [52:29](http://youtu.be/hdSrT4yjS1g?t=52m29s)

#### Reading / Watching

+ **What** is **REST**?
(if you haven't already read it, read the REST Wikipedia article):
http://en.wikipedia.org/wiki/Representational_state_transfer
+ The 5 Things Every API Must Have:
https://blog.newrelic.com/2014/09/08/apipunchlist/
+ Best Practices for Designing a Pragmatic RESTful API (***Great*** article)
http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
+ REST+JSON API Design - Best Practices for Developers
http://youtu.be/hdSrT4yjS1g (*comprehensive* overview)
+ Secure Your API - Tips for REST + JSON Developers
http://youtu.be/FeSdFhsKGG0
+ PUT vs POST in REST:
http://stackoverflow.com/questions/630453/put-vs-post-in-rest

#### Examples of Successful (Good) APIs

+ Parse REST API: https://www.parse.com/docs/rest
(really good example of good interactive documentation)
+ GitHub: https://developer.github.com/
+ Twitter: https://dev.twitter.com/rest/public
+ Google: https://developers.google.com/custom-search/json-api/v1/using_rest
+ Stripe: https://stripe.com/docs/api

#### Useful Resources

+ **lout** API documentation generator (for hapi.js apps):
https://github.com/hapijs/lout
+ RESTful web API Documentation Generator.
http://apidocjs.com
+ Swagger - The World's Most Popular Framework for APIs:
http://swagger.io

### Streaming

### WebSockets

#### Reading

+ **Q**: Can we use WebSockets? http://caniuse.com/#feat=websockets  
**Answer**: ***YES***! IE 10+, Safari/iOS Safari 7.1+, Android 4.4+ & Android Chrome
+ About WebSockets: https://www.websocket.org/aboutwebsocket.html
+ WebSocket MDN: https://developer.mozilla.org/en/docs/WebSockets
+ W3C WebSocket API: http://www.w3.org/TR/2011/WD-websockets-20110419/
+ CloudFlare WebSockets (good intro): https://blog.cloudflare.com/cloudflare-now-supports-websockets/
+ SitePoint article on WebSockets in HTML5:
http://www.sitepoint.com/introduction-to-the-html5-websockets-api/
+ Socket.io Chat Example (uses express): http://socket.io/get-started/chat/
+ Socket.io Max Connections? 250k:
http://stackoverflow.com/questions/10161796/how-many-users-nodejs-socket-io-can-support

#### Examples

+ Twitter Streaming API:
https://dev.twitter.com/streaming/overview
+ Salesforce Streaming API:
http://www.salesforce.com/developer/docs/api_streaming/


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

### Wrong way 1 – URL versioning

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

### Wrong way 3 - content type:

```sh
HTTP GET:
https://haveibeenpwned.com/api/breachedaccount/foo
Accept: application/vnd.haveibeenpwned.v2+json
```
### Further Reading (Versioning)

+ Pivotal Labs API Versioning guide: http://pivotallabs.com/api-versioning/
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
