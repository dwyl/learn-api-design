# Learn API Design

Essential learning for people building their own API

Starting a project "***from scratch***" is a opportunity
(and privilege *few* people get). If you are *fortunate* enough to be
in that position, do not take the task lightly.

A few quotes from
[Joshua Bloch](http://en.wikipedia.org/wiki/Joshua_Bloch)'s
Google Talk on
["***How To Design A Good API and Why it Matters***"](http://youtu.be/heh4OeB9A-c)  
and [Kevin Lacker](https://twitter.com/lacker)'s ([@Parse](https://parse.com/products)) ["***How to Design Great APIs***"](https://www.youtube.com/watch?v=qCdpTji8nxo)

> "*You have **one chance** to **get it right**.*" [3:17](http://youtu.be/heh4OeB9A-c?t=3m17s)

> "*A bad API can be amoung a company's greatest liabilities...
> can cause an un-ending stream of support phonecalls ...
and it can **inhibit** a company's **ability to move forward***" [2:51](http://youtu.be/heh4OeB9A-c?t=2m51s)

> "*Once you have a **bad** API, you **can't change it**,
you are pretty much **stuck with it forever**.*" [3:12](http://youtu.be/heh4OeB9A-c?t=2m51s)


> "* ... **A good API** needs to appeal to the most powerful emotion: **Laziness***". [3:23](http://youtu.be/qCdpTji8nxo?t=3m23s)

> "* You need to **be opinionated** even when **there is no right and wrong** *" [31:02](http://youtu.be/qCdpTji8nxo?t=31m2s)

## Characteristics of a Good API

+ ***Easy to learn*** (*notice the priority placement of learn-ability...*)
+ Intuitive / Easy to ***use*** even without documentation
+ ***Hard to misuse***.
+ Easy to read and maintain code that uses it
+ Sufficiently powerful to satisfy requirements
+ Easy to evolve
+ Appropriate to audience
+ ***Opinionated*** (means people don't have to *think*)


## Types of API

### REST

#### Reading

+ PUT vs POST in REST:
http://stackoverflow.com/questions/630453/put-vs-post-in-rest

#### Examples

+ Parse REST API: https://www.parse.com/docs/rest



### Streaming

### WebSockets

#### Reading

+ **Q**: Can I use WebSockets? http://caniuse.com/#feat=websockets  
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


## Versioning your API

+ Your API versioning is wrong:
http://www.troyhunt.com/2014/02/your-api-versioning-is-wrong-which-is.html
+ The debate on API versioning:
http://stackoverflow.com/questions/389169/best-practices-for-api-versioning

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

```
HTTP GET:
https://haveibeenpwned.com/api/breachedaccount/foo
Accept: application/vnd.haveibeenpwned.v2+json
```

## Background Reading + Watching

+ **BASIC** Introduction to APIs by [Derek Dahmer](https://github.com/ddgromit)
@ General Assembly:  
https://www.youtube.com/watch?v=FknvOGcLHmc (Google for Entrepreneurs) (*absolute beginner*?)
+ Wikipedia: http://en.wikipedia.org/wiki/Application_programming_interface
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
