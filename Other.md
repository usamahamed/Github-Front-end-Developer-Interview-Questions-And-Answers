Browser
==

## Glossary

- **BOM** - The Browser Object Model (BOM) is a browser-specific convention referring to all the objects exposed by the web browser. The `window` object is one of them.
- **CSSOM** - CSS Object Model.
- **DOM** - The Document Object Model (DOM) is a cross-platform and language-independent convention for representing and interacting with objects in HTML, XHTML, and XML documents.
- **Reflow** - When the changes affect document contents or structure, or element position, a reflow (or relayout) happens.
- **Repaint** - When changing element styles which don't affect the element's position on a page (such as `background-color`, `border-color`, `visibility`), the browser just repaints the element again with the new styles applied (that means a "repaint" or "restyle" is happening).
- **Composite** - TODO

## Rendering

High level flow of how browsers render a webpage:

1. DOM
  - The DOM (Document Object Model) is formed from the HTML that is received from a server.
  - Characters -> Tokens -> Nodes -> DOM.
  - DOM construction is incremental.
  - CSS and JS are requested as the respective `<link>` and `<script>` tags are encountered.
1. CSSOM
  - Styles are loaded and parsed, forming the CSSOM (CSS Object Model).
  - Characters -> Tokens -> Nodes -> CSSOM.
  - CSSOM construction is not incremental.
  - Browser blocks page rendering until it receives and processes all the CSS.
  - CSS is render blocking.
1. Render Tree
  - On top of DOM and CSSOM, a render tree is created, which is a set of objects to be rendered. Render tree reflects the DOM structure except for invisible elements (like the <head> tag or elements that have `display: none`; set). Each text string is represented in the rendering tree as a separate renderer. Each of the rendering objects contains its corresponding DOM object (or a text block) plus the calculated styles. In other words, the render tree describes the visual representation of a DOM.
1. Layout
  - For each render tree element, its coordinates are calculated, which is called "layout". Browsers use a flow method which only required one pass to layout all the elements (tables require more than one pass).
1. Painting
  - Finally, this gets actually displayed in a browser window, a process called "painting".

###### References

- http://taligarsiel.com/Projects/howbrowserswork1.htm
- https://medium.freecodecamp.org/its-not-dark-magic-pulling-back-the-curtains-from-your-stylesheets-c8d677fa21b2

## Repaint

When changing element styles which don't affect the element's position on a page (such as `background-color`, `border-color`, `visibility`), the browser just repaints the element again with the new styles applied (that means a "repaint" or "restyle" is happening).

## Reflow

When the changes affect document contents or structure, or element position, a reflow (or relayout) happens. These changes are usually triggered by:
- DOM manipulation (element addition, deletion, altering, or changing element order)
- Contents changes, including text changes in form fields
- Calculation or altering of CSS properties
- Adding or removing style sheets
- Changing the "class" attribute
- Browser window manipulation (resizing, scrolling); Pseudo-class activation (`:hover`)

#### References

- [How Browsers Work](http://taligarsiel.com/Projects/howbrowserswork1.htm)
- [What Every Frontend Developer Should Know About Webpage Rendering](http://frontendbabel.info/articles/webpage-rendering-101/)
- [Rendering: repaint, reflow/relayout, restyle](http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/)
- [Building the DOM faster: speculative parsing, async, defer and preload](https://hacks.mozilla.org/2017/09/building-the-dom-faster-speculative-parsing-async-defer-and-preload/)

Performance
==

WIP.

## Glossary

- **Critical Rendering Path** -
- `requestAnimationFrame`

## General Strategies

1. Minimize Bytes.
1. Reduce critical resources.
1. Reduce CRP length. TODO: Explain what CRP length is.

## Loading

- Minify, Compress, Cache assets.
- Browsers have a [preloader](https://andydavies.me/blog/2013/10/22/how-the-browser-pre-loader-makes-pages-load-faster/) to load assets ahead of time.

## Rendering

- Remove whitespace and comments from HTML/CSS/JS file via minification.
- CSS
  - CSS blocks rendering AND JavaScript execution.
  - Split up CSS for fewer rendering blocking CSS stylesheets by using media attributes.
    - Download only the necessary CSS before the browser can start to render.
    - https://developers.google.com/web/fundamentals/design-and-ui/responsive/#css-media-queries
  - Use Simpler selectors.
- JavaScript
  - JS blocks HTML parsing. If the script is external, it will have to be downloaded first. This incurs latency in network and execution.
  - Shift `<script>` tags to the bottom.
  - Async:
    - Scripts that don't modify the DOM or CSSOM can use the `async` attribute to tell the browser not to block DOM parsing and does not need to wait for the CSSOM to be ready.
  - Defer JavaScript execution:
    - There is also a `defer` attribute available. The difference is that with `defer`, the script waits to execute until after the document has been parsed, whereas `async` lets the script run in the background while the document is being parsed.
  - Use web workers for long running operations to move into a web worker thread.
  - Use `requestAnimationFrame`

###### References

- https://bitsofco.de/understanding-the-critical-rendering-path/

## Measuring

- [Navigation Timing API](https://developer.mozilla.org/en/docs/Web/API/Navigation_timing_API) is a JavaScript API for accurately measuring performance on the web. The API provides a simple way to get accurate and detailed timing statistics natively for page navigation and load events.
  - `performance.timing`: An object with the timestamps of the various events on the page. Some uses:
    - Network latency: `responseEnd` - `fetchStart`.
    - The time taken for page load once the page is received from the server: `loadEventEnd` - `responseEnd`.
    - The whole process of navigation and page load: `loadEventEnd` - `navigationStart`.

## Tools

- Yahoo YSlow
- Google PageSpeed Insights
- WebPageTest
- Sitespeed.io
- Google Lighthouse

## Web Performance Rules

- https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp
- http://stevesouders.com/hpws/rules.php
- https://developer.yahoo.com/performance/rules.html
- https://browserdiet.com/en/


Security
==

## Glossary

- **CORS** - Cross-Origin Resource Sharing (CORS).
- **CSRF** - Cross-Site request forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application in which they're currently authenticated.
- **XSS** - Cross-site scripting (XSS).

## CORS

The same-origin policy protects users by disallowing websites to retrieve information from other websites of different origins. An origin is the triple {protocol, host, port}. Two resources are considered to be of the same origin if and only if all these values are exactly the same.

Cross-Origin Resource Sharing allows relaxing of the same-origin policy. CORS defines a way in which a browser and server can interact to determine whether or not it is safe to allow the cross-origin request.

This standard extends HTTP with a new `Origin` request header and `Access-Control-Allow-Origin` and `Access-Control-Allow-Methods` response headers. It allows servers to use a header to explicitly list origins and HTTP methods that may request a file or to use a wildcard and allow a file to be requested by any site. `XMLHttpRequest`s to a target origin from a different source origin will be blocked if the server did not allow CORS for source origin.

## CSRF

XSS vulnerabilities allow attackers to bypass essentially all CSRF preventions.

#### Protection

- Verifying Same Origin with Standard Headers
  - There are two steps to this check:
    1. Determining the origin the request is coming from (source origin).
    2. Determining the origin the request is going to (target origin).
  - Examine the `Origin`, `Referer` and `Host` Header values.
- Synchronizer Tokens
  - The CSRF token is added as a hidden field for forms or within the URL.
  - Characteristics of a CSRF Token
    - Unique per user session
    - Large random value
    - Generated by a cryptographically secure random number generator
  - The server rejects the requested action if the CSRF token fails validation.
- Double Cookie
  - When a user visits a site, the site should generate a (cryptographically strong) pseudorandom value and set it as a cookie on the user's machine. The site should require every form submission to include this pseudorandom value as a form value and also as a cookie value. When a POST request is sent to the site, the request should only be considered valid if the form value and the cookie value are the same. When an attacker submits a form on behalf of a user, he can only modify the values of the form. An attacker cannot read any data sent from the server or modify cookie values, per the same-origin policy. This means that while an attacker can send any value he wants with the form, he will be unable to modify or read the value stored in the cookie. Since the cookie value and the form value must be the same, the attacker will be unable to successfully submit a form unless he is able to guess the pseudorandom value.
  - The advantage of this approach is that it requires no server state; you simply set the cookie value once, then every HTTP POST checks to ensure that one of the submitted <input> values contains the exact same cookie value. Any difference between the two means a possible XSRF attack.
- Cookie-to-Header Token
  - On login, the web application sets a cookie containing a random token that remains the same for the whole user session
    - `Set-Cookie: Csrf-token=i8XNjC4b8KVok4uw5RftR38Wgp2BFwql; expires=Thu, 23-Jul-2015 10:25:33 GMT; Max-Age=31449600; Path=/`
  - JavaScript operating on the client side reads its value and copies it into a custom HTTP header sent with each transactional request
    - `X-Csrf-Token: i8XNjC4b8KVok4uw5RftR38Wgp2BFwql`
  - The server validates presence and integrity of the token.
  - Security of this technique is based on the assumption that only JavaScript running within the same origin will be able to read the cookie's value.
  - JavaScript running from a rogue file or email will not be able to read it and copy into the custom header. Even though the `csrf-token` cookie will be automatically sent with the rogue request, the server will be still expecting a valid `X-Csrf-Token` header.
- Use of Custom Request Headers
  - An alternate defense which is particularly well suited for AJAX endpoints is the use of a custom request header. This defense relies on the same-origin policy (SOP) restriction that only JavaScript can be used to add a custom header, and only within its origin. By default, browsers don't allow JavaScript to make cross origin requests. Such a header can be `X-Requested-With: XMLHttpRequest`.
  - If this is the case for your system, you can simply verify the presence of this header and value on all your server side AJAX endpoints in order to protect against CSRF attacks. This approach has the double advantage of usually requiring no UI changes and not introducing any server side state, which is particularly attractive to REST services. You can always add your own custom header and value if that is preferred.
- Require user interaction
  - Require a re-authentication, using a one-time token, or requiring users to complete a captcha.

###### References

- [OWASP CSRF](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF))

## HTTPS

HTTPS is HTTP over SSL/TLS. Servers and clients still speak exactly the same HTTP to each other, but over a secure SSL connection that encrypts and decrypts their requests and responses. The SSL layer has 2 main purposes:

1. Verifying that you are talking directly to the server that you think you are talking to.
1. Ensuring that only the server can read what you send it and only you can read what it sends back.

#### TLS Handshake

// TODO. Crosscheck and add in more details.

1. The client computer sends a `ClientHello` message to the server with its Transport Layer Security (TLS) version, list of cipher algorithms and compression methods available.
1. The server replies with a `ServerHello` message to the client with the TLS version, selected cipher, selected compression methods and the server's public certificate signed by a CA (Certificate Authority). The certificate contains a public key that will be used by the client to encrypt the rest of the handshake until a symmetric key can be agreed upon.
1. The client verifies the server digital certificate against its list of trusted CAs. If trust can be established based on the CA, the client generates a string of pseudo-random bytes and encrypts this with the server's public key. These random bytes can be used to determine the symmetric key.
1. The server decrypts the random bytes using its private key and uses these bytes to generate its own copy of the symmetric master key.
1. The client sends a `Finished` message to the server, encrypting a hash of the transmission up to this point with the symmetric key.
1. The server generates its own hash, and then decrypts the client-sent hash to verify that it matches. If it does, it sends its own `Finished` message to the client, also encrypted with the symmetric key.
1. From now on the TLS session transmits the application (HTTP) data encrypted with the agreed symmetric key.

#### Downsides of HTTPS

- TLS handshake computational and latency overhead.
- Encryption and decryption requires more computation power and bandwidth.

###### References

- https://blog.hartleybrody.com/https-certificates/
- https://github.com/alex/what-happens-when#tls-handshake
- http://robertheaton.com/2014/03/27/how-does-https-actually-work/

## XSS

XSS vulnerabilities allow attackers to bypass essentially all CSRF preventions.

```js
const name = "<img src='x' onerror='alert(1)'>";
el.innerHTML = name;
```

http://shebang.brandonmintern.com/foolproof-html-escaping-in-javascript/

## Session hijacking

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies
- https://www.nczonline.net/blog/2009/05/12/cookies-and-security/


## Framebusting

https://seclab.stanford.edu/websec/framebusting/framebust.pdf

## API

https://github.com/shieldfy/API-Security-Checklist

# Talk about your understanding of front-end engineering

Front-end engineering is nothing more than two points, specification and automation.

Including team development specification, modular development, component development, component warehouse, performance optimization, deployment, testing, development process, development tools, scaffolding, git workflow, teamwork

1. Build tools 2. Continuous integration 3. System testing 4. Log statistics 5. On-line deployment 6. Agile development 7. Performance optimization 8. Fundamental framework

# Advantages and disadvantages of bidirectional binding and unidirectional data binding

Only UI controls exist only two-way, non-UI controls only one way. The advantage of unidirectional binding is that it can bring unidirectional data flow. The advantage is that the flow direction can be tracked, flowing in a single state, and there is no state, which makes it possible to avoid the problem of state management when the complexity increases , The commissioning of the program will become relatively easy. One-way data flow is more conducive to the maintenance and optimization of the state, more conducive to communication between components, more conducive to component reuse

Advantages of bidirectional data streams:
(CRD (Create, Retrieve, Update, Delete) operations that do not require unidirectional data binding; bidirectional binding in some situations that require real-time response to user input that is very user-friendly The changes in the view are automatically synchronized to the data model The change in the value of the data model will be immediately synchronized to the view;

Disadvantages:
The bi-directional data stream is an automatic management state, but there are many logic in the practical application that have to deal with the state change manually, so that the complexity of the program can not track the change of the local state, the bidirectional data flow, the value and the UI binding, Data interdependence is bound to each other, leading to the source of data problems difficult to be tracked

# Two ways to implement front-end routing

HTML5 History Two new APIs: history.pushState and history.replaceState, both APIs will operate the browser's history without causing page refreshes.

Hash is the url to see #, we need a monitor hash changes triggered by the event (hashchange) events. We do not re-render the page with the window.location, but instead use the new page in the history so that we can jump to the page to register the ajax in the hashchange event to change the page content. You can add a listening event for a change to a hash:

window.addEventListener("hashchange", funcRef, false)
advantage
From the point of view of performance and user experience, back-end routing sends a request to the server each time a new page is accessed, and the server responds to the request, and there is a delay in the process. And front-end routing in a new page when the visit is just a change of the path only, there is no network delay, for the user experience will be a considerable increase.

There are many advantages of front-end routing, such as page persistence, like most music sites, you can play the song at the same time, jump to another page and the music is not interrupted, such as the front and back completely separated. The development of a front-end routing, the main consideration to the page can be pluggable, the page life cycle, memory management.

Disadvantages
Use the browser forward, back button when the request will be re-sent, there is no reasonable use of the cache.

History interface provides two new methods: pushState(), replaceState()allows us to modify the browser history stack:
``
window.history.pushState(stateObject, title, URL)
window.history.replaceState(stateObject, title, URL)
``
# Browser Rendering Principle Resolution



1, the first rendering engine to download HTML, parsing DOM Tree generated

2, encounter css tags or JS script tags on the new thread to download them, and continue to build DOM. (Where css is an asynchronous download sync) The browser engine builds a Rendering Tree with DOM Tree and CSS Rule Tree

3, through the CSS Rule Tree to match the DOM Tree positioning coordinates and size, this process is called Flow or Layout.

4, the final process by calling the Native GUI API drawing page process called Paint.

When the user interacts with each other when browsing the web or changes the page structure through the js script, some of the above operations may run repeatedly. This process is called Repaint or Reflow. Rearrangement means that the dom tree structure changes, the need to rebuild the dom structure. Redrawing means that the dom node style changes and is redrawn. Rearrangement will bring redrawing, redrawing is not necessarily rearranged.

How to reduce the browser rearrangement: the elements that will need to be rearranged repeatedly, the position property is set to absolute or fixed, so that the element is out of the document flow and its changes do not affect the other elements.

## Restful

REST (Representational State Transfer) REST means characterization of state transition, is a kind of HTTP application based on the network application interface style, make full use of HTTP method to achieve a unified style interface services, HTTP defines the following eight standard methods:

GET: Request to get the specified resource
HEAD: Requests the response header of the specified resource
PUT: The request server stores a resource according to the REST design pattern, which is typically used to implement the following functions: GET, POST, PUT, DELETE,

# Talk about the observer pattern

JS in the realization of the observer pattern is achieved via a callback ,, which defines the relationship of one to many observers have multiple objects simultaneously monitor a particular theme objects

Observer pattern: a program in a real-time observation of the object, when the object state changes notify

Why do we use the observer pattern, can be achieved mainly loosely coupled code, what does that mean? That is, between the main body and subscribers are independent of each other, both of which can run independently.

# The difference between GET and POST

GET using a URL or Cookie mass participation, and POST data in BODY, this is because the HTTP protocol usage conventions. Not their own differences.
GET submission of data has a length limit, the POST data can be very large, this is because they are used to distinguish between different operating system and browser settings caused. Nor is the difference between GET and POST itself.
POST than GET security, because the data is not visible in the address bar, this argument is not wrong, but still not the difference between GET and POST itself.
The biggest difference between GET and POST GET request is mainly the idempotency, POST requests are not. (Idempotent: multiple requests for the same URL should return the same results.) Because the get request is idempotent, in the network of tunnels will not try and try again. If the request by data get, there will be the risk of repetitive operation, and this operation is repeated may lead to side effects

# Front-end rendering advantages

Partial refresh. You do not need to complete every page request
Lazy loading. As only the initial load when the page data in the visible region after scroll rp loading other data, can be achieved by react-lazyload
Rich interaction. Use JS achieve a variety of cool effects
Save server costs. Saving money, JS support for CDN deployment, and deployment is extremely simple and requires only the server can support static files
Natural separation of concerns design. Provide an interface to access the database server, JS only concerned with data acquisition and presentation
JS learn once, use everywhere. It can be used to develop Web, Serve, Mobile, Desktop types of applications

# The advantages of server-side rendering

Better SEO, because the search engine crawlers crawlers can view fully rendered page.

After the end of the service rendered do not need to download a bunch of js and css to see the page (the first screen performance)

Side rendering services without concern for browser compatibility issues (casual browser development, the advantage gradually disappear)

For the power not to force mobile phone or tablet, reducing the consumption of electricity in the client is very important


* Please describe the difference between `` `` `` `` `` `` `` ``

  A: The difference is as follows:
  * get to the specified resource request data, the requested data will be attached to the URL, that is, the data placed in the request line (request line)), to split the URL and transfer data, multiple parameters with &
  * post Submit the data to be processed to the specified resource. get method, the query request is displayed in the url, there is a length limit, get method is safe idempotent. The post method request is encapsulated in the http message body

   & | get | post
  --- | --- | ----
  Back / refresh | harmless | request to resubmit
  Bookmark | do bookmark | do not do
  Cache | can be cached | can not be cached
  History | keep in the browser record | not keep
  On data length limit | limit (2048 characters) | not limited
  Security | Visible data in url | Relatively safe
  Visible | visible in url | not visible

  to sum up:
    - For get, it is the server to request data, its request is visible in the url, its length is limited (2048 characters) individual method is safe idempotent, where security is used to obtain information rather than modify information, power And so on means that each request is the same result.
    - for the post, is to submit data to the server, each refresh or back will be re-submitted, post request data encapsulated in the http request header.
    
 ###   Why is it more efficient to use multiple domain names to store site resources?

CDN cache is more convenient 
Break the browser concurrency restrictions 
Save cookie bandwidth 
Saving the number of primary domain name connections, optimizing page response speed 
To prevent unnecessary security problems

## What are the image formats used to know how to create a web page?

　　Answer:

　　png-8, png-24, jpeg, gif, svg.

　　But none of the above is the last answer the interviewer wants. The interviewer wants to hear is Webp, Apng . (Whether it's concerned about new technology, new things)

　　Popular science Webp : WebP format, Google (google) developed a picture to speed up the image loading speed of the picture format. Picture compression volume is only about 2/3 of JPEG, and can save a lot of server bandwidth resources and data space. Facebook Ebay and other well-known sites have begun to test and use the WebP format.

　　In the same quality, WebP format images are 40% smaller than JPEG images.

　　Apng : full name is "Animated Portable Network Graphics" , PNG bitmap animation expansion, you can achieve png format dynamic picture effects. 04 was born, but has not been the major browser manufacturers support, until recently got iOS safari 8 support, is expected to replace the GIF as the next generation dynamic map standard.
# large number of pictures on the page (large electricity business website), loading is very slow, what methods do you have to optimize the loading of these pictures, give users a better experience.

Image lazy loading, in the page can not add a visible area of ​​a scroll bar event to determine the location of the picture and the top of the browser and the distance between the page, if the former is less than the latter, the priority load.
If you are using slides, albums, etc., you can use the image preload technology, the current display of the previous picture and a priority download.
If the picture for the css picture, you can use CSSsprite, SVGsprite, Iconfont, Base64 and other technologies.
If the picture is too large, you can use a special encoding of the picture, the load will first load a compressed special powerful thumbnails to improve the user experience.
If the image display area is smaller than the actual size of the picture, the image compression is followed by the image compression in front of the server according to the business needs. 

## How do you understand the semantics of HTML structures?　　

Removed or when the style is lost to make the page show a clear structure:
html itself is not performance, we see such as <h1> is bold, font size 2em, bold; <strong> is bold, do not think this is html performance, these in fact html default css style in the Role, so when the removal or style is lost when the page can make a clear structure is not the advantages of semantic HTML structure, but the browser has a default style, the default style is also intended to better express the semantics of html, it can be said The browser's default style and semantic HTML structure are inseparable.

The screen reader (if the visitor has a visually impaired) will "read" your page entirely based on your markup.
　　For example, if you use a semantic markup, the screen reader will "spell out your words one by one" instead of trying to pronounce it completely.

PDA, mobile phones and other devices may not be the same as the ordinary computer's browser to render the same page (usually because these devices support CSS is weak)

### Talk about the front end of the point of doing SEO need to consider what?

Learn how search engines crawl web pages and how to index web pages
　　You need to know the basic working principle of some search engines, the difference between the various search engines, search robot (SE robot or web crawler) how to work, how to search engine search results sort.

Meta tag optimization
　　It mainly includes Title, Website Description, and Keywords. There are other hidden words such as Author, Category, Language, and so on.

How to select keywords and place keywords in web pages
　　Search would have to use keywords. Keyword analysis and selection is one of SEO's most important jobs. First of all, to the site to determine the main keywords (usually in the five up and down), and then optimized for these keywords, including the keyword density (Density), relevance (Relavancy), highlight (Prominency) and so on.

Learn about the major search engines
　　Although there are many search engines, but the decision on the site traffic on the so few. Such as English, mainly Google, Yahoo, Bing, etc .; Chinese Baidu, Sogou, proper way. Different search engines on the page crawl and index, sort the rules are not the same. But also to understand the search portal and the relationship between search engines, such as AOL web search using Google's search technology, MSN is Bing's technology.

The main Internet directory
　　Open Directory itself is not a search engine, but a large site directory, he and the search engine is the main difference between the way the site content is collected in different ways. Directory is manually edited, mainly included site home page; search engine is automatically collected, in addition to the main page also crawls a lot of content pages.

Pay-per-click search engine
　　Search engines also need to survive, with the Internet business more and more mature, charging the search engine also began to flourish. The most typical of Overture and Baidu, of course, including Google's advertising program Google Adwords. More and more people through the search engine click advertising to locate the business site, which also has a great optimization and ranking of knowledge, you have to learn to use the least advertising to get the most clicks.

Search engine login
　　After the site is done, do not lie there waiting for the guests to fall from the sky. The easiest way to get someone to find you is to submit the site to the search engine. If you are a commercial site, the main search engine and directory will ask you to pay for the collection (such as Yahoo to 299 US dollars), but the good news is (at least so far) the largest search engine Google is still free, and it dominates With more than 60% of the search market.

Link Popularization and Link Popularity
　　Web content is hyperlinked to the way Hypertext (Hypertext), the same is true between sites. In addition to the search engine, people also surfing ("surfing") daily through links between different sites. The more links to other sites to your site, you will get more visits. What's more, the more the number of external links your site will be, the greater the importance of the search engine, and give you a higher ranking.

Use reasonable labels 
　　Use semantic tags to ensure that these devices render the web in a meaningful way. Ideally, the task of viewing the device is to match the device's own conditions to render the page.

　　The semantic markup provides the necessary information for the device, eliminating the need for yourself to consider all possible display situations (including existing or future new devices). For example, a cell phone can choose to make a title The text is displayed in bold, and the handheld may be displayed in a larger font. Whichever way you mark the text as a title, you can be sure that the reading device will display the page appropriately according to its own condition.

Search engine crawlers also rely on tags to determine the context and the weight of each keyword
　　In the past you may have not yet considered the search engine crawler is also the site of the "visitors", but now they are actually extremely valuable users. Without them, the search engine will not be able to index your site and then the average user will be hard to come over The

Whether your page is easy to understand the crawler is important, because the crawler will largely ignore the mark for the performance, but only focus on semantic markup.
　　Therefore, if the page file's title is marked instead of, then the page may be relatively backward in the search results. In addition to enhancing ease of use, the semantic markup facilitates the proper use of CSS and JavaScript, since it itself provides many "Hook" to apply the page style and behavior. 
SEO mainly depends on the content of your site and external links.

Easy to team development and maintenance
　　W3C gave us a very good standard, in the team we all follow this standard, you can reduce a lot of different things, easy to develop and maintain, improve development efficiency, and even achieve modular development .
  
  
