
- **Closure** - "Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope." - [YDKJS](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch5.md)
- **Event Loop** - The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the message queue. If the call stack is empty and there are callback functions in the message queue, a message is dequeued and pushed onto the call stack to be executed.
- **Hoisting** - "Wherever a var appears inside a scope, that declaration is taken to belong to the entire scope and accessible everywhere throughout." - [YDKJS](https://github.com/getify/You-Dont-Know-JS/blob/master/up%20%26%20going/ch2.md#hoisting)
- **Promise** - "The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value." - [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  - Promises can contain an immediate value.
- **Prototype** - TBD
- **This** - The `this` keyword does not refer to the function in which `this` is used or that function's scope. Javascript uses [4 rules](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md#determining-this) to determine if `this` will reference an arbitrary object, *undefined* or the *global* object inside a particular function call.

## Core Language

### Variables

- Reference: [Types and Grammar](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch1.md)
- Types
- Scopes
- [Coercion](https://github.com/getify/You-Dont-Know-JS/blob/master/up%20%26%20going/ch2.md#coercion)

### Functions

- Reference: [this & Object Prototypes](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch3.md)
- Declaration vs Expression
- Closures
- `.call`, `.apply` and `.bind`
- Currying
- Arrow functions and lexical this

### Prototypes and Objects

- Reference: [this & Object Prototypes](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/README.md#you-dont-know-js-scope--closures)
- Prototype chain
- `this` keyword
  - https://rainsoft.io/gentle-explanation-of-this-in-javascript/
  - https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3
- Classes
  - Methods
    - Use non-arrow functions for methods that will be called using the `object.method()` syntax because you need the value of `this` to point to the instance itself.

### Async

- Reference: [Async and Peformance](https://github.com/getify/You-Dont-Know-JS/blob/master/async%20&%20performance/README.md#you-dont-know-js-async--performance)
- `setTimeout`, `setInterval` and event loop
  - [setImmediate() vs nextTick() vs setTimeout(fn,0)](http://voidcanvas.com/setimmediate-vs-nexttick-vs-settimeout/)
- Event Loop
- Debounce and Throttle
  - Throttling enforces a maximum number of times a function can be called over time.
  - Debouncing enforces that a function not be called again until a certain amount of time has passed without it being called.
  - https://css-tricks.com/debouncing-throttling-explained-examples/
- Callbacks
- [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) and [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) in ES7

**Reference**

- https://www.vikingcodeschool.com/falling-in-love-with-javascript/the-javascript-event-loop

## Design Patterns

- https://addyosmani.com/resources/essentialjsdesignpatterns/book/

## Strict Mode

1. Strict mode eliminates some JavaScript silent errors by changing them to throw errors.
1. Strict mode fixes mistakes that make it difficult for JavaScript engines to perform optimizations. Strict mode code can sometimes be made to run faster than identical code that's not strict mode.
1. Strict mode prohibits some syntax likely to be defined in future versions of ECMAScript.

**Converting Mistakes into Errors**

- Prevent accidental creation of global variables.
- Makes assignments which would otherwise silently fail throw an exception.
- Makes attempts to delete undeletable properties throw errors.
- Requires that all properties named in an object literal be unique. Duplicate property names are a syntax error in strict mode.
- Requires that function parameter names be unique. In normal code the last duplicated argument hides previous identically-named arguments.
- Forbids setting properties on primitive values in ES6. Without strict mode, setting properties is simply ignored (no-op), with strict mode, however, a `TypeError` is thrown.

**Simplifying Variable Uses**

- Prohibits `with`.
- `eval` of strict mode code does not introduce new variables into the surrounding scope.
- Forbids deleting plain variables. `delete` name in strict mode is a syntax error: `var x; delete x; // !!! syntax error`.

**Paving the way for future ECMAScript versions**

- Future ECMAScript versions will likely introduce new syntax, and strict mode in ECMAScript 5 applies some restrictions to ease the transition. It will be easier to make some changes if the foundations of those changes are prohibited in strict mode.
- First, in strict mode a short list of identifiers become reserved keywords. These words are `implements`, `interface`, `let`, `package`, `private`, `protected`, `public`, `static`, and `yield`. In strict mode, then, you can't name or use variables or arguments with these names.



- Second, strict mode prohibits function statements not at the top level of a script or function.



## HTML Questions

Answers to [Front-end Job Interview Questions - HTML Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions#html-questions). Pull requests for suggestions and corrections are welcome!

### What does a `doctype` do?

`doctype` is an abbreviation for document type. It is a declaration used in HTML5 to distinguish between a standards-compliant parsing mode and a quirks parsing mode. Hence its presence tells the browser to parse and render the webpage in standards mode.

Moral of the story - just add `<!DOCTYPE html>` at the start of your page.

###### References

- https://stackoverflow.com/questions/7695044/what-does-doctype-html-do
- https://www.w3.org/QA/Tips/Doctype
# What is semantic HTML?

Intuitive awareness tags are good for crawling search engines and doing the right thing with the right tags! 
html semantics is to make the contents of the page structure, easy to the browser, search engine resolution; 
in the case of no CCS case is also a document format display, and is easy to read. The search engine crawler relies on the markup to determine the context and the weight of each keyword, which is good for SEO. 
So that people who read the source code more likely to site the site block, easy to read maintenance understanding.

### What's the difference between full standards mode, almost standards mode and quirks mode?

- **Quirks mode** - Layout emulates non-standard behavior in Netscape Navigator 4 and Internet Explorer 5. This is essential in order to support websites that were built before the widespread adoption of web standards. The list of quirks can be found [here](https://developer.mozilla.org/en-US/docs/Mozilla/Mozilla_quirks_mode_behavior).
- **Full standards mode** - The layout behavior is the one described by the HTML and CSS specifications.
- **Almost standards mode** - There are only a very small number of quirks implemented. Differences can be found [here](https://developer.mozilla.org/en-US/docs/Gecko's_Almost_Standards_Mode).

###### References

- https://developer.mozilla.org/en-US/docs/Quirks_Mode_and_Standards_Mode

### What's the difference between HTML and XHTML?

XHTML belongs to the family of XML markups languages and is different from HTML. Some of differences are as follows:

- XHTML documents have to be well-formed, unlike HTML, which is more forgiving.
- XHTML is case-sensitive for element and attribute names, while HTML is not.
- Raw `<` and `&` characters are not allowed except inside of `CDATA` Sections (`<![CDATA[ ... ]]>`). JavaScript typically contains characters which can not exist in XHTML outside of CDATA Sections, such as the `<` operator. Hence it is tricky to use inline `styles` or `script` tags in XHTML and should be avoided.
- A fatal parse error in XML (such as an incorrect tag structure) causes document processing to be aborted.

Full list of differences can be found on [Wikipedia](https://en.wikipedia.org/wiki/XHTML#Relationship_to_HTML).

###### References

- https://developer.mozilla.org/en-US/docs/Archive/Web/Properly_Using_CSS_and_JavaScript_in_XHTML_Documents_
- https://en.wikipedia.org/wiki/XHTML

### Are there any problems with serving pages as `application/xhtml+xml`?

Basically the problems lie in the differences between parsing HTML and XML as mentioned above.

- XHTML, or rather, XML syntax is less forgiving and if your page isn't fully XML-compliant, there will be parsing errors and users get unreadable content.
- Serving your pages as `application/xhtml+xml` will cause Internet Explorer 8 to show a download dialog box for an unknown format instead of displaying your page, as the first version of Internet Explorer with support for XHTML is Internet Explorer 9.

###### References

- https://developer.mozilla.org/en-US/docs/Quirks_Mode_and_Standards_Mode#XHTML

## What is the Quirks mode? What is the difference between it and the Standards model?

　　Answer:

　　Starting with IE6, the Standards model was introduced. In standard mode, the browser tried to get the correct processing of the standard document to the specified level in the specified browser.

　　IE6 before IE is not mature enough, so IE5 browser before the CSS support is poor, IE6 will provide better support for CSS, but then the problem came, because there are many pages based on the old layout Way to write, and if IE6 support CSS will make these pages display is not normal, how to ensure that does not destroy the existing page, but also provide a new rendering mechanism?

　　In the process of writing we will often encounter such a problem, how to ensure that the original interface unchanged, but also provide more powerful features, especially when the new features are not compatible with the old features. One common practice when dealing with this problem is to add parameters and branches, that is, when a parameter is true, we use the new function, and if this parameter is not true, the use of old features, so that can not destroy The original program, but also provide new features. IE6 is similar to this, it will DTD as the "parameters", because the previous page we will not write DTD, so IE6 assumes that if you write a DTD, it means that this page will be used to support CSS better Of the layout, and if not, then the use of compatible with the layout before. This is the Quirks mode (quirks mode, weird mode, weird mode).

　　the difference:

　　There will be layout, style analysis and script implementation of the three differences.
  
 ## a: img alt and title What is the same? b: strong and em similarities and differences?

　　Answer:

　　a:

alt (alt text): User agent (UA) for which images, forms, or applets can not be displayed, and the alt attribute is used to specify replacement text. The language of the replacement text is specified by the lang attribute. (In the IE browser will be no title when the alt as tool tip display)
title (tool tip): This attribute provides the recommended information for the element that sets the attribute.
　　b:

strong: bold emphasis on the label, stressed that the importance of the content
em: italic emphasis on the label, more strongly stressed that the contents of the emphasis points



### How do you serve a page with content in multiple languages?

The question is a little vague, I will assume that it is asking about the most common case, which is how to serve a page with content available in multiple languages, but the content within the page should be displayed only in one consistent language.

When an HTTP request is made to a server, the requesting user agent usually sends information about language preferences, such as in the `Accept-Language` header. The server can then use this information to return a version of the document in the appropriate language if such an alternative is available. The returned HTML document should also declare the `lang` attribute in the `<html>` tag, such as `<html lang="en">...</html>`.

In the back end, the HTML markup will contain `i18n` placeholders and content for the specific language stored in YML or JSON formats. The server then dynamically generates the HTML page with content in that particular language, usually with the help of a back end framework.

###### References

- https://www.w3.org/International/getting-started/language

### What kind of things must you be wary of when designing or developing for multilingual sites?

- Use `lang` attribute in your HTML.
- Directing users to their native language - Allow a user to change his country/language easily without hassle.
- Text in images is not a scalable approach - Placing text in an image is still a popular way to get good-looking, non-system fonts to display on any computer. However to translate image text, each string of text will need to have it's a separate image created for each language. Anything more than a handful of replacements like this can quickly get out of control.
- Restrictive words / sentence length - Some content can be longer when written in another language. Be wary of layout or overflow issues in the design. It's best to avoid designing where the amount of text would make or break a design. Character counts come into play with things like headlines, labels, and buttons. They are less of an issue with free flowing text such as body text or comments.
- Be mindful of how colors are perceived - Colors are perceived differently across languages and cultures. The design should use color appropriately.
- Formatting dates and currencies - Calendar dates are sometimes presented in different ways. Eg. "May 31, 2012" in the U.S. vs. "31 May 2012" in parts of Europe.
- Do not concatenate translated strings - Do not do anything like `"The date today is " + date`. It will break in languages with different word order. Using template parameters instead.
- Language reading direction - In English, we read from left-to-right, top-to-bottom, in traditional Japanese, text is read up-to-down, right-to-left.

###### References

- https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites

### What are `data-` attributes good for?

Before JavaScript frameworks became popular, front end developers used `data-` attributes to store extra data within the DOM itself, without other hacks such as non-standard attributes, extra properties on the DOM. It is intended to store custom data private to the page or application, for which there are no more appropriate attributes or elements.

These days, using `data-` attributes is not encouraged. One reason is that users can modify the data attribute easily by using inspect element in the browser. The data model is better stored within JavaScript itself and stay updated with the DOM via data binding possibly through a library or a framework.

###### References

- http://html5doctor.com/html5-custom-data-attributes/
- https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes

### Consider HTML5 as an open web platform. What are the building blocks of HTML5?

- Semantics - Allowing you to describe more precisely what your content is.
- Connectivity - Allowing you to communicate with the server in new and innovative ways.
- Offline and storage - Allowing webpages to store data on the client-side locally and operate offline more efficiently.
- Multimedia - Making video and audio first-class citizens in the Open Web.
- 2D/3D graphics and effects - Allowing a much more diverse range of presentation options.
- Performance and integration - Providing greater speed optimization and better usage of computer hardware.
- Device access - Allowing for the usage of various input and output devices.
- Styling - Letting authors write more sophisticated themes.

###### References

- https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5

### Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

All the above mentioned technologies are key-value storage mechanisms on the client side. They are only able to store values as strings.

|  |`cookie`|`localStorage`|`sessionStorage`|
|--|--|--|--|
| Initiator | Client or server. Server can use `Set-Cookie` header | Client | Client |
| Expiry | Manually set | Forever | On tab close |
| Persistent across browser sessions | Depends on whether expiration is set | Yes | No |
| Have domain associated | Yes | No | No |
| Sent to server with every HTTP request| Cookies are automatically being sent via `Cookie` header | No | No |
| Capacity (per domain) | 4kb | 5MB | 5MB |
| Accessibility | Any window | Any window | Same tab |

###### References

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies
- http://tutorial.techaltum.com/local-and-session-storage.html

### Describe the difference between `<script>`, `<script async>` and `<script defer>`.

- `<script>` - HTML parsing is blocked, the script is fetched and executed immediately, HTML parsing resumes after the script is executed.
- `<script async>` - The script will be fetched in parallel to HTML parsing and executed as soon as it is available (potentially before HTML parsing completes). Use `async` when the script is independent of any other scripts on the page, for example analytics.
- `<script defer>` - The script will be fetched in parallel to HTML parsing and executed when the page has finished parsing. If there are multiple of them, each deferred script is executed in the order they were encoun­tered in the document. If a script relies on a fully-parsed DOM, the `defer` attribute will be useful in ensuring that the HTML is fully parsed before executing. There's not much difference from putting a normal `<script>` at the end of `<body>`. A deferred script must not contain `document.write`.

Note: The `async` and `defer` attrib­utes are ignored for scripts that have no `src` attribute.

###### References

- http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html
- https://stackoverflow.com/questions/10808109/script-tag-async-defer
- https://bitsofco.de/async-vs-defer/

### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

**Placing `<link>`s in the `<head>`**

Putting `<link>`s in the head is part of the specification. Besides that, placing at the top allows the page to render progressively which improves user experience. The problem with putting stylesheets near the bottom of the document is that it prohibits progressive rendering in many browsers, including Internet Explorer. Some browsers block rendering to avoid having to repaint elements of the page if their styles change. The user is stuck viewing a blank white page. It prevents the flash of unstyled contents.

**Placing `<script>`s just before `</body>`**

`<script>`s block HTML parsing while they are being downloaded and executed. Downloading the scripts at the bottom will allow the HTML to be parsed and displayed to the user first.

An exception for positioning of `<script>`s at the bottom is when your script contains `document.write()`, but these days it's not a good practice to use `document.write()`. Also, placing `<script>`s at the bottom means that the browser cannot start downloading the scripts until the entire document is parsed. One possible workaround is to put `<script>` in the `<head>` and use the `defer` attribute.

###### References

- https://developer.yahoo.com/performance/rules.html#css_top

# Talk about JavaScript scope chain

When you execute a JavaScript code (global code or function), the JavaScript engine creates a scope for it, also known as the Execution Context, which first creates a global scope after the page loads, and then each time a function , Will establish a corresponding scope, which formed a scope chain. Each scope has a corresponding scope chain, the chain head is the global scope, the chain is the current function scope. 
The role of the scope chain is used to parse the identifier. When the function is created (not executed), all the local variables in this and arguments are added to the current scope, and when JavaScript needs to be found Variable X (this process is called variable analysis), it will first from the scope chain chain is the current scope of the search for whether there is X attribute, if not found along the scope chain to continue to find, until the search To the chain header, that is, the global scope chain, still found the variable, then that the code does not exist on the scope of the x variable variable, and throw a reference error (ReferenceError) exception.

# How to understand the JavaScript prototype chain

Every object in JavaScript has a prototype property, which we call the prototype, and the prototype value is an object, so it also has its own prototype, so that it is a prototype chain, the chain of the chain is the object, Its prototype is special, the value is null. 
The prototype function is used for object inheritance, and the prototype property of function A is an object. When this function is used as a constructor to create an instance, the prototype property of the function is assigned as a prototype to all object instances , Such as we create a new array, the array of methods from the array of inheritance from the prototype. 
When you access a property of the object, the first look for the object itself, find the return; if not found, then continue to find the properties of its prototype object (if not found in fact, along the prototype chain to find up until the root) The As long as there is no coverage, the object prototype properties can be found in all instances, if the entire prototype is not found to return undefined

### What is progressive rendering?

Progressive rendering is the name given to techniques used to improve performance of a webpage (in particular, improve perceived load time) to render content for display as quickly as possible.

It used to be much more prevalent in the days before broadband internet but it is still useful in modern development as mobile data connections are becoming increasingly popular (and unreliable)!

Examples of such techniques:

- Lazy loading of images - Images on the page are not loaded all at once. JavaScript will be used to load an image when the user scrolls into the part of the page that displays the image.
- Prioritizing visible content (or above-the-fold rendering) - Include only the minimum CSS/content/scripts necessary for the amount of page that would be rendered in the users browser first to display as quickly as possible, you can then use deferred scripts or listen for the `DOMContentLoaded`/`load` event to load in other resources and content.
- Async HTML fragments - Flushing parts of the HTML to the browser as the page is constructed on the back end. More details on the technique can be found [here](http://www.ebaytechblog.com/2014/12/08/async-fragments-rediscovering-progressive-html-rendering-with-marko/).

###### References

- https://stackoverflow.com/questions/33651166/what-is-progressive-rendering
- http://www.ebaytechblog.com/2014/12/08/async-fragments-rediscovering-progressive-html-rendering-with-marko/

### Have you used different HTML templating languages before?

Yes, Pug (formerly Jade), ERB, Slim, Handlebars, Jinja, Liquid, just to name a few. In my opinion, they are more or less the same and provide similar functionality of escaping content and helpful filters for manipulating the data to be displayed. Most templating engines will also allow you to inject your own filters in the event you need custom processing before display.

### Other Answers

- https://neal.codes/blog/front-end-interview-questions-html/
- http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/

## CSS Questions

Answers to [Front-end Job Interview Questions - CSS Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions#css-questions). Pull requests for suggestions and corrections are welcome!

### What is the difference between classes and IDs in CSS?

- **IDs** - Meant to be unique within the document. Can be used to identify an element when linking using a fragment identifier. Elements can only have one `id` attribute.
- **Classes** - Can be reused on multiple elements within the document. Mainly for styling and targeting elements.

###### References
- https://www.w3.org/TR/CSS1/#id-as-selector
- https://www.w3.org/TR/CSS1/#class-as-selector

### What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

- **Resetting** - Resetting is meant to strip all default browser styling on elements. For e.g. `margin`s, `padding`s, `font-size`s of all elements are reset to be the same. You will have to redeclare styling for common typographic elements.
- **Normalizing** - Normalizing preserves useful default styles rather than "unstyling" everything. It also corrects bugs for common browser dependencies.

I would choose resetting when I have very a customized or unconventional site design such that I need to do a lot of my own styling do not need any default styling to be preserved.

###### References

- https://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css

### Describe `float`s and how they work.

Float is a CSS positioning property. Floated elements remain a part of the flow of the page, and will affect the positioning of other elements (e.g. text will flow around floated elements), unlike `position: absolute` elements, which are removed from the flow of the page.

The CSS `clear` property can be used to be positioned below `left`/`right`/`both` floated elements.

If a parent element contains nothing but floated elements, its height will be collapsed to nothing. It can be fixed by clearing the float after the floated elements in the container but before the close of the container.

The `.clearfix` hack uses a clever CSS pseudo selector (`:after`) to clear floats. Rather than setting the overflow on the parent, you apply an additional class `clearfix` to it. Then apply this CSS:

```css
.clearfix:after {
  content: ' ';
  visibility: hidden;
  display: block;
  height: 0;
  clear: both;
}
```

Alternatively, give `overflow: auto` or `overflow: hidden` property to the parent element which will establish a new block formatting context inside the children and it will expand to contain its children.

###### References

# write the following code in each browser in the color value?
```
background : red; // firefox 
_background : green; // IE6 
* background : blue; // IE6, IE7
 background : black \ 9 ; // IE6 --- IE10
```
# Add some css to its level vertically.

Use line-height=height
```
< div style = "` text-align: center; line-height: 200px; height: 200px; width: 200px; `" >  Yan Haijing </ div >
```
# to achieve a preloading picture, loaded after the show is displayed in the page and set its height of 50px, width of 50px;
```
function preloadPics (ARRS) { 
        varARR = [];
        varthe callback = function () {};
        varindex =0;
         function AddIndex () { 
            index ++;
            if (index == arrs.length) {
                callback ();
            }
        }
        for ( var i = 0 ; i <arrs.length; i ++) {
            arr [i] = new Image ();
            arr [i] .src = arrs [i];
            arr [i] .onload = function () {  
                addIndex ();
            }
        }
        return {
            done: function (c) {
                callback = c || callback
            }
        }

    }
    preloadPics ([ 'a.jpg' ]). done ( function () { 
        console .log ( 'load done' );
    });
```

# simulation of a HashTable class, including add, remove, contains, length method;
```
function HashTable () { 
        this.arr = [];
    }
    HashTable.prototype.add = function (data) { 
        this .arr.push (data);
    };
    HashTable.prototype.remove = function (i) { 
        if ( this .arr [i]) { delete  this .arr [i]; return  true ;}
         return  false ;
    };
    HashTable.prototype.contains = function (data) { 
        var index = this .arr.indexOf (data);
         if (index! == - 1 ) { return  true ;}
         else { return  false ;}
    };
    HashTable.prototype.length = function () { 
        return  this .arr.length;
    };
    var c = new HashTable ();
    c.add ( 'apple' );
    c.add ( 'peach' );
    c.add ( 'plum' );
```

# JS how to achieve object-oriented and inheritance mechanism?

Constructor inheritance, prototyping inheritance, hybrid inheritance, parasitic inheritance

The first three are class inheritance, the last one is the object inheritance. (The interviewer is so different. Although I do not recognize)

# Constructor inheritance
```
function Super (a) { 
    this.a = a;
    this.func = function () {};
}
function Sub (a) { 
    Super.call (this, a);
}
var obj = new Sub ();
obj {
    a: undefined ,
    func: function () { }
}
```
Prototype inheritance
```
function Super (a) { 
    this.a = a;
    this.func = function () {};
}
function Sub () { 
}
Sub.prototype = new Super ();
Sub.prototype.constructor = Sub;
var obj = new Sub ();
obj {__proto __: {a: undefined , func: function () {} ,
         constructor : function Sub () {} }} 
 ```
 
Mixed inheritance
```
function Super (a) { 
    this.a = a;
    this.func = function () {};
}
function Sub (a) { 
    Super.call (this, a);
}
Sub.prototype = new Super ();
Sub.prototype.constructor = Sub;
var obj = new Sub ();
obj {a: undefined , func: function () {} ,
    __proto__: {a: undefined , func: function () {} ,
         constructor : function Sub () {} }} 
   ```
   
Parasitic inheritance
```
function Super (a) { 
    this.a = a;
    this.func = function () {};
}
Super.prototype.talk = function () { console .log ( 'talk' );}
 function Sub (a) {  
    Super.call ( this , a);
}
Sub.prototype = Object .create (Super.prototype);
Sub.prototype.constructor = Sub;
var obj = new Sub ();
obj { a : undefined, func: function () { },
    __ proto__ : { constructor : function Sub () { },
        __ proto__ : { talk : function () {console. log ( 'talk' ) ; }
             constructor : function  Super () { }
        }

    }
}
```
# JS module packaging methods, such as how to achieve private variables, can not be directly assigned, only through public methods;

Object-oriented private member
```
function P (pwd) { 
    varpassword = pwd;
     function getPasswd () {  
        returnpassword;
    }
    this .pwdService = function () { 
        return getPasswd ();
    }
}
P.prototype.checkPwd = function (pwd) { 
    return  this .pwdService () === pwd;
}
Protect pwd and getPwd, leaving only the check interface

var P = new new P ( '1111' );
 Console .log (p.checkPwd ( '1111' ));     //  to true 
Console .log (p.password)    // undefined 
Console .log (p.getPassword ())     / / Type error p.getPassword () is  not a function 
console .log (p.getPassword)   // undefined
```

# the understanding of the closure, the benefits and disadvantages of closure?

An internal function that accesses an external function variable.

Advantages : You can simulate some of the features of oo (design private methods and variables. Make some more advanced js applications). Can prevent contamination between modules. Cache. 
Anonymous self-executing functions, anonymous self-executing functions can reduce memory consumption.

Disadvantages : possession of memory can not be released.

Closures require more memory than the average function. Especially in the IE browser need attention. Because IE uses non-native javascript objects to implement DOM objects, closures can cause memory leaks, for example:
```
function A () {   
      vara =document.createElement ("div"),//
            msg ="Hello";  
       a.onclick = function () {  
          alert (msg);  
          }  
   }  
 A ();
 ```

(Such as aleert (msg)), the function function (alert () () () () () () () () () () () () () () () () () () () () () () () () msg)) quotes ScopeA, which is a circular reference that will cause memory leaks in IE.

# How to implement an EventEmitter
```
var util = require ('util');
var EventEmitter = require ('events');
functionMyEmitter () {
    EventEmitter.call (this);
} // Constructor
util.inherits (MyEmitter, EventEmitter); // inherited
var em = new MyEmitter ();
em.on ('hello', function (data) {
    console.log ('receive event hello data:', data);
}); // receive the event and print it to the console
em.emit ('hello', 'EventEmitter send the message really convenient!');
```
# Use node to simulate client-initiated requests
```
var http = require ("http");
var request = http.request ({
    host: "localhost",
    port: "8080"
    path: "/ request",
    method: "post"
}, function (res) {
    res.on ("data", function (chunk) {
        console.log (chunk.toString ());
    });
});
request.write ("user = zhang & pass = 111");
request.end ("request end"); // end this request
```
# Mark and sweep
This is the most common form of garbage collection in JavaScript. When a variable enters the execution environment, such as a variable in a function, the garbage collector marks it as an "entry environment", and when the variable leaves the environment (the end of the function) Marked as "leaving the environment".

The garbage collector will mark all the variables stored in memory at run time, then remove the variables in the environment and the variables (closures) that are referenced by the variables in the environment. After these completions, the tag is still Delete the variable

# Reference counting
In the low version of IE often there will be memory leaks, often because it uses the reference count for garbage collection. The method of referencing the count is to track the number of times each value is used for the record. When a variable is declared and a reference type is assigned to the variable, the number of references to this value is incremented by 1 if the value of the variable becomes another , This is worth the number of references minus 1, when the value of the number of references to 0, indicating that no variables in use, this value can not be accessed, so it can take up space for recycling, so garbage collector will Run the time to clean up the reference number of 0 occupied by the value of space.


# What is Etag?

When sending a server request, the browser will first cache outdated judgment. The browser determines whether the cache file expires based on the cache expiration time.
Scenario 1: If there is no expiration, do not send the request to the server, the direct use of the results in the cache, then we can see in the browser console  200 OK(from cache), this time the situation is full use of the cache, the browser and server There is no interaction.

Scenario 2: If it has expired, send a request to the server, where the request will bring the file modification time set in ①, andEtag

Then, the resource update judgment is made. The server according to the browser over the file to modify the time to determine the browser since the last request, the file is not not modified; according Etagto judge the contents of the file since the last request, there has been no change

Case 1: If the two kinds of conclusions are judged file has not been modified, the server is not sent to the browser index.html's content, and tell it, the document has not been modified, you use your right side of the cache -  304 Not Modified, At this point the browser will be from the local cache to get index.htmlthe content. In this case, the protocol cache is called, and there is a request interaction between the browser and the server.
Case 2: If you modify the time and the contents of the document to determine any one did not pass, the server will accept the request, after the operation with the ①

# What is the HTTP request message structure?

rfc2616 has been defined:

The first line is the Request-Line including: request method , request URI , protocol version , CRLF
The first line is followed by a number of row request headers , including general-header , request-header or entity-header , each line ends with CRLF
There is a CRLF delimited between the request header and the message entity
According to the actual request may contain a message entity A request message example is as follows:

# HTTP response What is the message structure?

rfc2616 has been defined:

The first line is the status line including: HTTP version, status code, status description , followed by a CRLF
The first line is followed by a number of rows of response headers , including: generic head, response head, solid head
The response header and the response entity are separated by a CRLF blank line
Finally, a possible message entity response message example is as follows:
## What is the outer margin overlap? What is the result of the overlap?

　　Answer:

　　The outer margin is margin-collapse.

　　In CSS, the outer margins of two adjacent boxes (which may be brotherly relationships may also be ancestral relationships) can be combined into a separate margin. This way of merging the outer margins is called folding, and thus the bounds of the outer margins are called folded outer margins.

　　The folding results follow the following calculation rules:

When two adjacent outer margins are positive, the result of folding is a large value between them .
When two adjacent outer margins are negative, the result of the folding is a larger value of the absolute value of the two .
When the two margins are positive and negative, the result of the folding is the sum of the two .

- https://css-tricks.com/all-about-floats/

### Describe `z-index` and how stacking context is formed.

The `z-index` property in CSS controls the vertical stacking order of elements that overlap. `z-index` only effects elements that have a `position` value which is not `static`.

Without any `z-index` value, elements stack in the order that they appear in the DOM (the lowest one down at the same hierarchy level appears on top). Elements with non-static positioning (and their children) will always appear on top of elements with default static positioning, regardless of HTML hierarchy.

A stacking context is an element that contains a set of layers. Within a local stacking context, the `z-index` values of its children are set relative to that element rather than to the document root. Layers outside of that context — i.e. sibling elements of a local stacking context — can't sit between layers within it. If an element B sits on top of element A, a child element of element A, element C, can never be higher than element B even if element C has a higher `z-index` than element B.

Each stacking context is self-contained - after the element's contents are stacked, the whole element is considered in the stacking order of the parent stacking context. A handful of CSS properties trigger a new stacking context, such as `opacity` less than 1, `filter` that is not `none`, and `transform that is not `none`.

###### References

- https://css-tricks.com/almanac/properties/z/z-index/
- https://philipwalton.com/articles/what-no-one-told-you-about-z-index/
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context



### Describe Block Formatting Context (BFC) and how it works.

A Block Formatting Context (BFC) is part of the visual CSS rendering of a web page in which block boxes are laid out. Floats, absolutely positioned elements, `inline-blocks`, `table-cells`, `table-caption`s, and elements with `overflow` other than `visible` (except when that value has been propagated to the viewport) establish new block formatting contexts.

A BFC is an HTML box that satisfies at least one of the following conditions:

- The value of `float` is not `none`.
- The value of `position` is neither `static` nor `relative`.
- The value of `display` is `table-cell`, `table-caption`, `inline-block`, `flex`, or `inline-flex`.
- The value of `overflow` is not `visible`.

In a BFC, each box's left outer edge touches the left edge of the containing block (for right-to-left formatting, right edges touch).

Vertical margins between adjacent block-level boxes in a BFC collapse. Read more on [collapsing margins](https://www.sitepoint.com/web-foundations/collapsing-margins/).

###### References

- https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Block_formatting_context
- https://www.sitepoint.com/understanding-block-formatting-contexts-in-css/

### What are the various clearing techniques and which is appropriate for what context?

- Empty `div` method - `<div style="clear:both;"></div>`.
- Clearfix method - Refer to the `.clearfix` class above.
- `overflow: auto` or `overflow: hidden` method - Parent will establish a new block formatting context and expand to contains its floated children.

In large projects, I would write a utility `.clearfix` class and use them in places where I need it. `overflow: hidden` might clip children if the children is taller than the parent and is not very ideal.

### Explain CSS sprites, and how you would implement them on a page or site.

CSS sprites combine multiple images into one single larger image. It is commonly used technique for icons (Gmail uses it). How to implement it:

1. Use a sprite generator that packs multiple images into one and generate the appropriate CSS for it.
1. Each image would have a corresponding CSS class with `background-image`, `background-position` and `background-size` properties defined.
1. To use that image, add the corresponding class to your element.

**Advantages:**

- Reduce the number of HTTP requests for multiple images (only one single request is required per spritesheet). But with HTTP2, loading multiple images is no longer much of an issue.
- Advance downloading of assets that won't be downloaded until needed, such as images that only appear upon `:hover` pseudo-states. Blinking wouldn't be seen.

###### References

- https://css-tricks.com/css-sprites/

### What are your favorite image replacement techniques and which do you use when?

CSS image replacement is a technique of replacing a text element (usually a header tag like an `<h1>`) with an image (often a logo). It has its origins in the time before web fonts and SVG. For years, web developers battled against browser inconsistencies to craft image replacement techniques that struck the right balance between design and accessibility.

It's not really relevant these days. Check out the link below for all the available techniques.

###### References

- https://css-tricks.com/the-image-replacement-museum/

### How would you approach fixing browser-specific styling issues?

- After identifying the issue and the offending browser, use a separate style sheet that only loads when that specific browser is being used. This technique requires server-side rendering though.
- Use libraries like Bootstrap that already handles these styling issues for you.
- Use `autoprefixer` to automatically add vendor prefixes to your code.
- Use Reset CSS or Normalize.css.

### How do you serve your pages for feature-constrained browsers? What techniques/processes do you use?

- Graceful degradation - The practice of building an application for modern browsers while ensuring it remains functional in older browsers.
- Progressive enhancement - The practice of building an application for a base level of user experience, but adding functional enhancements when a browser supports it.
- Use [caniuse.com](https://caniuse.com/) to check for feature support.
- Autoprefixer for automatic vendor prefix insertion.
- Feature detection using [Modernizr](https://modernizr.com/).

### What are the different ways to visually hide content (and make it available only for screen readers)?

These techniques are related to accessibility (a11y).

- `visibility: hidden`. However the element is still in the flow of the page, and still takes up space.
- `width: 0; height: 0`. Make the element not take up any space on the screen at all, resulting in not showing it.
- `position: absolute; left: -99999px`. Position it outside of the screen.
- `text-indent: -9999px`. This only works on text within the `block` elements.
- Metadata. For example by using Schema.org, RDF and JSON-LD.
- WAI-ARIA. A W3C technical specification that specifies how to increase the accessibility of web pages.

Even if WAI-ARIA is the ideal solution, I would go with the `absolute` positioning approach, as it has the least caveats, works for most elements and it's an easy technique.

###### References

- https://www.w3.org/TR/wai-aria-1.1/
- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA
- http://a11yproject.com/

### Have you ever used a grid system, and if so, what do you prefer?

I like the `float`-based grid system because it still has the most browser support among the alternative existing systems (flex, grid). It has been used in Bootstrap for years and has been proven to work.

### Have you used or implemented media queries or mobile-specific layouts/CSS?

Yes. An example would be transforming a stacked pill navigation into a fixed-bottom tab navigation beyond a certain breakpoint.

### Are you familiar with styling SVG?

No... Sadly.

### How do you optimize your webpages for print?

- Create a stylesheet for print or use media queries.

```html
<!-- Main stylesheet on top -->
<link rel="stylesheet" href="/global.css" media="all" />
<!-- Print only, on bottom -->
<link rel="stylesheet" href="/print.css" media="print" />
```

Make sure to put non-print styles inside `@media screen { ... }`.

```css
@media print {
  ...
}
```

- Deliberately add page breaks.

```html
<style>
.page-break {
  display: none;
  page-break-before: always;
}
</style>

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Fusce eu felis. Curabitur sit amet magna. Nullam aliquet. Aliquam ut diam...
<div class="page-break"></div>
Lorem ipsum dolor sit amet, consectetuer adipiscing elit....
```

###### References

- https://davidwalsh.name/optimizing-structure-print-css


# What is the relationship between prototype and __proto__ : js __proto__ prototype and the difference between the relationship?

__proto __ (Implicit Prototype) and prototype (Explicit Prototype)
作者：苏墨橘
链接：https://www.zhihu.com/question/34183746/answer/59043879
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

What is it Explicit prototype explicit prototype property:After each function is created, it will have a property named prototype that points to the prototype object of the function. Note : The exception is the function built using the Function.prototype.bind method, which has no prototype property. (thank@ Chen Yu Lu Students answer let me know this)NOTE Function objects created using Function.prototype.bind do not have a prototype property or the [[Code]], [[FormalParameters]], and [[Scope]] internal properties. ----- ECMAScript Language SpecificationImplicit prototype link implicit prototype link:Any object in JavaScript has a built-in property [[prototype]]. There is no standard way to access this built-in property before ES5, but most browsers support access via __proto__. The Get method Object.getPrototypeOf () for this built-in attribute is available in ES5                      Note: The Object.prototype object is an exception with a __proto__ value of nullThe relationship between the two:An implicit prototype points to the prototype of the constructor that created this objectWhat is the role? The role of explicit prototyping: used to achieve prototype-based inheritance and attribute sharing.ECMAScript does not use classes such as those in C ++, Smalltalk, or Java. Instead objects may be created in various ways including via a literal notation or via constructors which create objects and then execute code that initialize all or part of them by assigning initial values each constructor is a function that has a property named "prototype" that is used to implement prototype-based inheritance and shared properties .Objects are created by using constructors in new expressions; for example, new Date (2009,11) creates a new Date object. ---- ECMAScript Language SpecificationThe role of implicit prototyping: Constitute a prototype chain, also used to achieve prototype-based inheritance. For example, when we access the x property in obj this object, if it is not found in obj, it looks in __proto__ order.Every object created by a constructor has an implicit reference (called the object's prototype) to the value of its constructor's "prototype" ---- ECMAScript Language Specification3. __proto__ pointing __proto__ point in the end how to judge it? According to ECMA definition 'to the value of its constructor's' prototype '' - an explicit prototype of the function that created this object. So the key point is to find the constructor that created this object. Now let's take a look at the way objects are created in JS. There are three ways to look at the past: (1) how the object literals (2) new 3) Object.create () in ES5 But I think there is essentially only one way to do this, which is to create it with new. Why do you say that, first of all, the literal approach is a syntactic sugar that makes it easier for developers to create objects, essentially var o = new Object (); o.xx = xx; o.yy = yy; Object.create (), which is a new method in ES5, before this is called prototype inheritance,Douglas wrote an article in 2006 titled Prototypal Inheritance In JavaScript. In this article, he introduced a way to achieve inheritance, this method does not use the strict constructor. His idea is that with the help of a prototype, you can create a new object based on an existing object, and you can create a custom type for that purpose. To do this, he gives the following function:         function object(o){
    function F(){}
    F.prototype = o;
    return new F()
}
 ----- "JavaScript Advanced Programming" P169So from the implementation of the code return new F () we can see that this is still created by new. The difference is that the object created by Object.create () does not have a constructor, see here you are not asking, there is no constructor how do I know where its __proto__ point, in fact, here it says there is no constructor is Refers to the constructor that we can not access outside of the Object.create () function, however it is present in the internal implementation of the function, which briefly exists for a while. Assuming we are inside the function now, we can see that the constructor of the object is F, now
```
var f = new F(); 
//于是有
f.__proto__ === F.prototype //true
//又因为
F.prototype === o;//true
//所以
f.__proto__ === o;
```
So the object created by Object.create (o) has its implicit prototype pointing to o. Well, the analysis of the way to create an object is over, and now you should be able to determine an object __proto__ point to whom.Well, let's take a look at some more puzzling examples to consolidate. Implicit prototype of the constructor's display prototype:Built-in objects: such as Array (), Array.prototype .__ What does proto__ point to? Array.prototype is also an object, the object is created by the Object () constructor Array.prototype .__ proto__ === Object.prototype / / true, or you can understand that all the built-in objects are Object () To create it.Custom object   1. By default:function Foo(){}
var foo = new Foo()
Foo.prototype.__proto__ === Object.prototype //true 理由同上
  2. Other cases: (1) function Bar(){}
//这时我们想让Foo继承Bar
Foo.prototype = new Bar()
 Foo.prototype.__proto__ === Bar.prototype //true
(2)//我们不想让Foo继承谁，但是我们要自己重新定义Foo.prototype
Foo.prototype = {
  a:10,
  b:-10
}
//这种方式就是用了对象字面量的方式来创建一个对象，根据前文所述 
Foo.prototype.__proto__ === Object.prototype
Note : Both of these are equivalent to completely overriding Foo.prototype, so the Foo.prototype.constructor is also changed. As a result, the constructor property is also disconnected from the original constructor Foo (). Implicit prototype of constructor Since it is a constructor then it is an instance of Function (), so it points to Function.prototype as Object .__ proto__ === Function.prototype4 instanceof instanceof operator's internal implementation mechanism and implicit prototype, explicit prototype has a direct relationship. The lvalue of instanceof is generally an object, the right value is generally a constructor, used to determine whether the lvalue is an instance of the right value. Its internal implementation principle is this://设 L instanceof R 
//通过判断
 L.__proto__.__proto__ ..... === R.prototype ？
//最终返回true or false
That is, the __proto__ along L is always looking for the end of the prototype chain until it equals R.prototype. Know this, you know why the following strange expressions get the corresponding value Function instanceof Object // true 
```
Object instanceof Function // true 
 Function instanceof Function //true
 Object instanceof Object // true
 Number instanceof Number //false
 ```


### What are some of the "gotchas" for writing efficient CSS?

Firstly, understand that browsers match selectors from rightmost (key selector) to left. Browsers filter out elements in the DOM according to the key selector, and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector. Hence avoid key selectors that are tag and universal selectors. They match a large numbers of elements and browsers will have to do more work in determining if the parents do match.

[BEM (Block Element Modifier)](https://bem.info/) methodology recommends that everything has a single class, and, where you need hierarchy, that gets baked into the name of the class as well, this naturally makes the selector efficient and easy to override.

Be aware of which CSS properties trigger reflow, repaint and compositing. Avoid writing styles that change the layout (trigger reflow) where possible.

###### References

- https://developers.google.com/web/fundamentals/performance/rendering/
- https://csstriggers.com/

### What are the advantages/disadvantages of using CSS preprocessors?

**Advantages:**

- CSS is made more maintainable.
- Easy to write nested selectors.
- Variables for consistent theming. Can share theme files across different projects.
- Mixins to generate repeated CSS.
- Splitting your code into multiple files. CSS files can be split up too but doing so will require a HTTP request to download each CSS file.

**Disadvantages:**

- Requires tools for preprocessing. Re-compilation time can be slow.

### Describe what you like and dislike about the CSS preprocessors you have used.

**Likes:**

- Mostly the advantages mentioned above.
- Less is written in JavaScript, which plays well with Node.

**Dislikes:**

- I use Sass via `node-sass`, which is a binding for LibSass written in C++. I have to frequently recompile it when switching between node versions.
- In Less, variable names are prefixed with `@`, which can be confused with native CSS keywords like `@media`, `@import` and `@font-face` rule.

### How would you implement a web design comp that uses non-standard fonts?

Use `@font-face` and define `font-family` for different `font-weight`s.

### Q: Is the CSS attribute case sensitive?

 ```
 ul {
     MaRGin: 10px;
 }
 ```
A: No distinction. HTML, CSS are case-insensitive, but in order to better readability and team collaboration are generally lowercase, and in XHTML elements in the name and attributes must be lowercase.

### Q: Inline element setting margin-topand margin-bottomwhether it works?

A: does not work. (The answer is working, and I feel wrong.)

The elements in html are divided into replaced elements and non-replaced elements.

A replacement element is an element that is used as a placeholder for other content. The most typical is imgthat it just points to an image file. As well as most form elements are also replaced, for example input.
A non-replacement element is an element that contains content in a document. For example, if a paragraph's text is placed within the element itself, the paragraph is a non-replacement element.
Discussion margin-topand margin-bottomwhether the elements within the line play a role, it is necessary to replace the elements and non-replacement elements within the line were discussed.

First, we should be aware that the outer margin can be applied to the inline elements, which is allowed in the specification, but because there is no effect on the line-height applied to the outer edge of the non-replacement element in a row. Since the outer margin is actually transparent. So the statement margin-topand margin-bottomno visual effect. The reason for this is that the outer margin of the non-replacement element in the row does not change the row height of an element. And for the row of non-replacement elements of the left and right margins is not the case, is influential.

The outer margin set for the replacement element will affect the row height, which may increase or decrease the row height, depending on the value of the upper and lower margins. The left and right margins of the inline substitution elements are the same as the left and right margins of the non-replacement elements. Take a look at demo:

http://codepen.io/paddingme/pen/JwCDF

### Q: Does the inline element set padding-topand padding-bottomincrease its height? (Where setting is padding-top and padding-bottom on an inline element add to its dimensions?)

A: The answer is no. With the title of the more tangled, do not understand the meaning of the square is in the end what is the meaning? Put aside, let's analyze the next. For inline elements, set the left and right margins, the left and right margins will be visible. And set the upper and lower margins, set the background color can be seen after the edge area has increased, for the line does not replace the elements, will not affect the line high, will not stretch the parent element. For the replacement element, the parent element is distracted. Look at the demo, a better understanding:

http://codepen.io/paddingme/pen/CnFpa

### Q: Set pof font-size:10remwhen the user resets or drag the browser window, whether the text size will also change with?

A: No.

remIs the relative unit of measure based on the size of the htmlroot element, and font-sizethe size of the text does not change as the size of the window changes.

### Q: The pseudo-class selector :checkedwill be used with or without the inputtype .radiocheckboxoption

A: No

checkedThe definition of the pseudo-class selector is obvious:

At The: the checked CSS pseudo-class Selector Represents by the any Radio ( <input type="radio">), the CheckBox ( <input type="checkbox">) or the Option ( <option>in A <select>) Element that IS the checked or s toggled to AN ON State at The the User CAN Change the this State by clicking ON at The Element, or the Selecting A Different. value, in which case the: checked pseudo-class no longer cases to this element, but will to the relevant one.
### Q: In the HTML text, the pseudo-class :rootalways points to the htmlelement?

A: No (the answer is given == ||). The following excerpts : root and html in CSS3 refers to the same element? s answer:

The root of a single finger. This root may not be html, if it is fragment html, did not create the root, then the root of the fragment. The following URL to support the data URL to see the browser (Firefox, Chrome, Safari, Opera), can be seen:
data:application/xhtml+xml,<div xmlns="http://www.w3.org/1999/xhtml"><style>:root { background: green; } html { background: red !important; }</style></div>
### Q: translate()Can the method move the position of an element on the z-axis?

A: No. translate()The method can only change the displacement on the x-axis and y-axis.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
ul {color:red;}
li {color:blue;}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
ul {color:red;}
#must-buy {color:blue;}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
.shopping-list .favorite {
    color: red;
}
#must-buy {
    color: blue;
}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
ul#awesome {
    color: red;
}
ul.shopping-list li.favorite span {
    color: blue;
}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
ul#awesome #must-buy {
    color: red;
}
.favorite span {
    color: blue!important;
}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
ul.shopping-list li .highlight {
    color: red;
}
ul.shopping-list li .highlight:nth-of-type(odd) {
    color: blue;
}
A: blue.

### Q: Is the color of the text "Sausage" in the following code?

<ul class="shopping-list" id="awesome">
    <li><span>Milk</span></li>
    <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
</ul>
#awesome .favorite:not(#awesome) .highlight {
    color: red;
}
#awesome .highlight:nth-of-type(1):nth-last-of-type(1) {
    color: blue;
}
A: blue.

## Q: #exampleHow does the location change:

<p id="example">Hello</p>
#example {margin-bottom: -5px;}
A: move up 5px.

## Q: #exampleHow does the location change:

<p id="example">Hello</p>
#example {margin-left: -5px;}
A: Move 5px to the left.

#i-am-useless Will it be loaded by the browser?

<div id="test1">
    <span id="test2"></span>
</div>
#i-am-useless {background-image: url('mypic.jpg');}
A: No

mypic.jpg Will it be loaded by the browser?

<div id="test1">
    <span id="test2"></span>
</div>
#test2 {
    background-image: url('mypic.jpg');
    display: none;
}
A: will be downloaded.

mypic.jpg Will it be loaded by the browser?

<div id="test1">
    <span id="test2"></span>
</div>
#test1 {
    display: none;
}
#test2 {
    background-image: url('mypic.jpg');
    visibility: hidden;
}
A: will not be downloaded.

## Q: onlyDoes the selector work?

@media only screen and (max-width: 1024px) {argin: 0;}
A: Stop the old version of the browser to parse the rest of the selector.

only used to set a specific type of media that can be used to exclude browsers that do not support media queries. In fact, only a lot of time is used for those who do not support Media Query but support Media Type device hidden style sheet. There are devices that support media properties (Media Queries), the normal call style, this time when it does not exist; for does not support the media properties (Media Queries) but also supports the media type (Media Type) equipment, so that Do not read the style, because it first read only and not screen; also does not support Media Qqueries browser, whether or not support only, the style will not be used.

## Q: overfloa:hiddenDoes the new block-level formatting context be formed?

<div>
    <p>I am floated</p>
    <p>So am I</p>
</div>
div {overflow: hidden;}
p {float: left;}
A: will be formed.

The conditions that will trigger BFC are:

The value of float is none.
overflow value is not visible.
The display value is any of the table-cell, table-caption, and inline-blocks.
The value of position is not relative and static.
## Q: screenDoes the keyword mean the size of the device's physical screen or the browser's window?

@media only screen and (max-width: 1024px) {margin: 0;}
A: browser window

Summary of knowledge points

Tips: According to the above test points under the following knowledge points, the latter will write articles to summarize, here only pick out the key to analysis.

For the CSS selector and the knowledge of the priority, see the following article:

CSS selector reference manual
CSS selector notes
Advanced CSS Style Selector
Conquer the advanced CSS selector
Detailed CSS selector, priority and matching principle
priority
Remember the use of 31 CSS selectors
# How to calculate the priority:

So how do you calculate the priority of the specified selector? If you consider that the four numbers separated by commas are preferred, such as 1, 1, 1, 1, or 0, 2, 0, 1
The first number (a) is usually 0 unless the style attribute is used on the label;
The second number (b) is the sum of the number of ids on the selector;
The third number (c) is the sum of the other attribute selectors and pseudo classes used on the selector. This includes class (.example) and attribute selectors (for example li[id=red]);
The fourth number (d) calculates the elements (like table, p, div, etc.) and pseudo elements (like first-line)
The general selector (*) is 0 priority;
If the two selectors have the same priority, the latter in the style sheet works.
Browser CSS Matching order:

The browser CSS does not look from left to right, but from right to left. For example #divBox p span.red{color:red;}, the browser to find the order is as follows: first search html all class = 'red' span element, find, and then find their parent elements in the p element, and then determine whether the parent of the p id is divBox div elements, if they are present. The right thing to look for from right to left is to filter out unrelated style rules and elements as early as possible.

display:noneAnd visibilty:hiddenthe difference between:


# Q: <keygen> is the correct HTML5 tag?

A: Yes.

The <keygen> tag specifies the key pair generator field for the form. When the form is submitted, the private key is stored locally and the public key is sent to the server. Is the HTML5 tag.

# Q: Can the <bdo> tag change the text orientation?

A: Yes.

The <bdo> tag overrides the default text orientation.

<bdo dir = "rtl"> Here is some text </ bdo>
# Q: Is the following HTML code correct?

<figure>
    <img src = "myimage.jpg" alt = "My image">
    <figcaption>
        <p> This is my self portrait. </ p>
    </ figcaption>
</ figure>
A: Right

The <figure> tag specifies separate stream content (images, charts, photos, codes, etc.). The contents of the figure element should be related to the main content, but if deleted, the document flow should not be affected. Use the <figcaption> element to add a caption to the figure.

# Q: Which case should I use the small tag? When you want to create a subtitle after the h1 title Or when the footer inside the increase in copyright information?

A: small labels General use scenes are used in copyright information and legal texts, or you can use annotation extensions (visible in bootstrap) in the title, but can not be used to create subtitles.

The HTML small element (<small>) makes the text font size one size smaller (for example, from large to medium, or from small to x-small) down to the browser's smallest font size. In HTML5, this element is repurposed to represent side-comments and small print, including copyright and legal text, independent of its styled presentation.
  
# Q: in a well-structured web page, a number of h1 tags will not help SEO?

A: No effect.

According to Matt Cutts (lead of Google's webspam team and the de facto expert on these things), using multiple <h1> tags is fine, as long as you're not abusing it (like sticking your whole page in an <h1> and using CSS to style it back to normal size. That would have no effect, and might trigger a penalty, as it looks spammy.
If you have multiple headings and it would be natural to use multiple <h1> 's, then go for it.
From: http://www.quora.com/Does-using-multiple-h1-tags-on-a-page-affect-search-engine-rankings

# Q: If you have a search results page, you want to highlight the search keywords. What HTML tags can I use?

A: The <mark> tag highlights the text.

The HTML is not used in a particular context. For example it can be used in a page showing search results to highlight every instance of the searched for word.
# Q: What is the scope attribute in the following code?

<article>
    <h1> Hello World </ h1>
    <style scoped>
        p {
            color: # FF0;
        }
    </ style>
    <p> This is my text </ p>
</ article>

<article>
    <h1> This is awesome </ h1>
    <p> I am some other text </ p>
</ article>
A: The scoped property is a boolean property. If you use this property, the style is applied only to the parent element of the style element and its child elements.

Does HTML5 support block-level hyperlinks? E.g:

<article>
    <a href="#">
        <h1> Hello </ h1>
        <p> I am some text </ p>
    </a>
</ article>
A: support.

The <a> element in HTML5 is represented as a hyperlink that supports any inline elements and block-level elements.

# Q: Will the new HTTP request be triggered when the following HTML code is loaded?

<img src = "mypic.jpg" style = "visibility: hidden" alt = "My picture">
A: it will be wow

# Q: Will the new HTTP request be triggered when the following HTML code is loaded?

<div style = "display: none;">
    <img src = "mypic.jpg" alt = "My photo">
</ div>
A: Yes!

will main1.css be loaded and compiled in alert ('Hello world')?

<head>
    <link href = "main1.css" rel = "stylesheet">
    <script>
        alert ('Hello World');
    </ script>
</ head>
A: Yes!

# Q: before the main2.css get1 must be downloaded analysis?

<head>
    <link href = "main1.css" rel = "stylesheet">
    <link href = "main2.css" rel = "stylesheet">
</ head>
A: no!

# Q: will the main2.css be loaded after Paragraph 1 is loaded?

<head>
    <link href = "main1.css" rel = "stylesheet">
</ head>
<body>
    <p> Paragraph 1 </ p>
    <p> Paragraph 2 </ p>
    <link href = "main2.css" rel = "stylesheet">
</ body>
A: yes!



### Explain how a browser determines what elements match a CSS selector.

This part is related to the above about writing efficient CSS. Browsers match selectors from rightmost (key selector) to left. Browsers filter out elements in the DOM according to the key selector, and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector.

For example with this selector `p span`, browsers firstly find all the `<span>` elements, and traverse up its parent all the way up to the root to find the `<p>` element. For a particular `<span>`, as soon as it finds a `<p>`, it knows that the `<span>` matches and can stop its matching.

###### References

- https://stackoverflow.com/questions/5797014/why-do-browsers-match-css-selectors-from-right-to-left

### Describe pseudo-elements and discuss what they are used for.

A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They can be used for decoration (`:first-line`, `:first-letter`) or adding elements to the markup (combined with `content: ...`) without having to modify the markup (`:before`, `:after`).

- `:first-line` and `:first-letter` can be used to decorate text.
- Used in the `.clearfix` hack as shown above to add a zero-space element with `clear: both`.
- Triangular arrows in tooltips use `:before` and `:after`. Encourages separation of concerns because the triangle is considered part of styling and not really the DOM. It's not really possible to draw a triangle with just CSS styles without using an additional HTML element.

###### References

- https://css-tricks.com/almanac/selectors/a/after-and-before/

### Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.

The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. Each box has a content area (e.g. text, an image, etc.) and optional surrounding `padding`, `border`, and `margin` areas.

The CSS box model is responsible for calculating:

- How much space a block element takes up.
- Whether or not borders and/or margins overlap, or collapse.
- A box's dimensions.

The box model has the following rules:

- The dimensions of a block element are calculated by `width`, `height`, `padding`, `border`s, and `margin`s.
- If no `height` is specified, a block element will be as high as the content it contains, plus `padding` (unless there are floats, for which see below).
- If no `width` is specified, a non-floated block element will expand to fit the width of its parent minus `padding`.
- The `height` of an element is calculated by the content's `height`.
- The `width` of an element is calculated by the content's `width`.
- By default, `padding`s and `border`s are not part of the `width` and `height` of an element.

###### References

- https://www.smashingmagazine.com/2010/06/the-principles-of-cross-browser-css-coding/#understand-the-css-box-model

### What does `* { box-sizing: border-box; }` do? What are its advantages?

- By default, elements have `box-sizing: content-box` applied, and only the content size is being accounted for.
- `box-sizing: border-box` changes how the `width` and `height` of elements are being calculated, `border` and `padding` are also being included in the calculation.
- The `height` of an element is now calculated by the content's `height` + vertical `padding` + vertical `border` width.
- The `width` of an element is now calculated by the content's `width` + horizontal `padding` + horizontal `border` width.

### List as many values for the `display` property that you can remember.

- `none`, `block`, `inline`, `inline-block`, `table`, `table-row`, `table-cell`, `list-item`.

### What's the difference between `inline` and `inline-block`?

I shall throw in a comparison with `block` for good measure.

|  |`block`|`inline-block`|`inline`|
|--|--|--|--|
| Size | Fills up the width of its parent container. | Depends on content. | Depends on content. |
| Positioning | Start on a new line and tolerates no HTML elements next to it (except when you add `float`) | Flows along with other content and allows other elements beside. | Flows along with other content and allows other elements beside. |
| Can specify `width` and `height` | Yes | Yes | No. Will ignore if being set. |
| Can be aligned with `vertical-align` | No | Yes | Yes |
| Margins and paddings | All sides respected. | All sides respected. | Only horizontal sides respected. Vertical sides, if specified, do not affect layout. Vertical space it takes up depends on `line-height`, even though the `border` and `padding` appear visually around the content. |
| Float | - | - | Becomes like a `block` element where you can set vertical margins and paddings. |

**What's the difference between a `relative`, `fixed`, `absolute` and `static`-ally positioned element?**

A positioned element is an element whose computed `position` property is either `relative`, `absolute`, `fixed` or `sticky`.

- `static` - The default position; the element will flow into the page as it normally would. The `top`, `right`, `bottom`, `left` and `z-index` properties do not apply.
- `relative` - The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
- `absolute` - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
- `fixed` - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.
- `sticky` - Sticky positioning is a hybrid of relative and fixed positioning. The element is treated as `relative` positioned until it crosses a specified threshold, at which point it is treated as `fixed` positioned.

###### References

- https://developer.mozilla.org/en/docs/Web/CSS/position

### The 'C' in CSS stands for Cascading. How is priority determined in assigning styles (a few examples)? How can you use this system to your advantage?

Browser determines what styles to show on an element depending on the specificity of CSS rules. We assume that the browser has already determined the rules that match a particular element. Among the matching rules, the specificity, four comma-separate values, `a, b, c, d` are calculated for each rule based on the following:

1. `a` is whether inline styles are being used. If the property declaration is an inline style on the element, `a` is 1, else 0.
2. `b` is the number of ID selectors.
3. `c` is the number of classes, attributes and pseudo-classes selectors.
4. `d` is the number of tags and pseudo-elements selectors.

The resulting specificity is not a score, but a matrix of values that can be compared column by column. When comparing selectors to determine which has the highest specificity, look from left to right, and compare the highest value in each column. So a value in column `b` will override values in columns `c` and `d`, no matter what they might be. As such, specificity of `0,1,0,0` would be greater than one of `0,0,10,10`.

In the cases of equal specificity: the latest rule is the one that counts. If you have written the same rule into your style sheet (regardless of internal or external) twice, then the lower rule in your style sheet is closer to the element to be styled, it is deemed to be more specific and therefore will be applied.

I would write CSS rules with low specificity so that they can be easily overridden if necessary. When writing CSS UI component library code, it is important that they have low specificities so that users of the library can override them without using too complicated CSS rules just for the sake of increasing specificity or resorting to `!important`.

###### References

- https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/
- https://www.sitepoint.com/web-foundations/specificity/

### What existing CSS frameworks have you used locally, or in production? How would you change/improve them?

- **Bootstrap** - Slow release cycle. Bootstrap 4 has been in alpha for almost 2 years. Add a spinner button component, as it is widely-used.
- **Semantic UI** - Source code structure makes theme customization extremely hard to understand. Painful to customize with unconventional theming system. Hardcoded config path within the vendor library. Not well-designed for overriding variables unlike in Bootstrap.
- **Bulma** - A lot of non-semantic and superfluous classes and markup required. Not backward compatible. Upgrading versions breaks the app in subtle manners.

### Have you played around with the new CSS Flexbox or Grid specs?

Yes. Flexbox is mainly meant for 1-dimensional layouts while Grid is meant for 2-dimensional layouts.

Flexbox solves many common problems in CSS, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap and Bulma are based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before but ran into some browser incompatibility issues (Safari) in using `flex-grow`, and I had to rewrite my code using `inline-blocks` and math to calculate the widths in percentages, it wasn't a nice experience.

Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.

###### References

- https://philipwalton.github.io/solved-by-flexbox/

### How is responsive design different from adaptive design?

Both responsive and adaptive design attempt to optimize the user experience across different devices, adjusting for different viewport sizes, resolutions, usage contexts, control mechanisms, and so on.

Responsive design works on the principle of flexibility - a single fluid website that can look good on any device. Responsive websites use media queries, flexible grids, and responsive images to create a user experience that flexes and changes based on a multitude of factors. Like a single ball growing or shrinking to fit through several different hoops.

Adaptive design is more like the modern definition of progressive enhancement. Instead of one flexible design, adaptive design detects the device and other features, and then provides the appropriate feature and layout based on a predefined set of viewport sizes and other characteristics. The site detects the type of device used, and delivers the pre-set layout for that device. Instead of a single ball going through several different-sized hoops, you'd have several different balls to use depending on the hoop size.

###### References

- https://developer.mozilla.org/en-US/docs/Archive/Apps/Design/UI_layout_basics/Responsive_design_versus_adaptive_design
- http://mediumwell.com/responsive-adaptive-mobile/
- https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/

### Have you ever worked with retina graphics? If so, when and what techniques did you use?

I tend to use higher resolution graphics (twice the display size) to handle retina display. The better way would be to use a media query like `@media only screen and (min-device-pixel-ratio: 2) { ... }` and change the `background-image`.

For icons, I would also opt to use svgs and icon fonts where possible, as they render very crisply regardless of resolution.

Another method would be to use JavaScript to replace the `<img>` `src` attribute with higher resolution versions after checking the `window.devicePixelRatio` value.

###### References

- https://www.sitepoint.com/css-techniques-for-retina-displays/

### Is there any reason you'd want to use `translate()` instead of `absolute` positioning, or vice-versa? And why?

`translate()` is a value of CSS `transform`. Changing `transform` or `opacity` does not trigger browser reflow or repaint, only compositions, whereas changing the absolute positioning triggers `reflow`. `transform` causes the browser to create a GPU layer for the element but changing absolute positioning properties uses the CPU. Hence `translate()` is more efficient and will result in shorter paint times for smoother animations.

When using `translate()`, the element still takes up its original space (sort of like `position: relative`), unlike in changing the absolute positioning.

###### References

- https://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/

### Other Answers

- https://neal.codes/blog/front-end-interview-css-questions
- https://quizlet.com/28293152/front-end-interview-questions-css-flash-cards/
- http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/

## JS Questions

Answers to [Front-end Job Interview Questions - JS Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions#js-questions). Pull requests for suggestions and corrections are welcome!

### Explain event delegation

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. The benefits of this technique are:

- Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
- There is no need to unbind the handler from elements that are removed and to bind the event for new elements.

###### References

- https://davidwalsh.name/event-delegate
- https://stackoverflow.com/questions/1687296/what-is-dom-event-delegation

### Explain how `this` works in JavaScript

There's no simple explanation for `this`; it is one of the most confusing concepts in JavaScript. A hand-wavey explanation is that the value of `this` depends on how the function is called. I have read many explanations on `this` online, and I found [Arnav Aggrawal](https://medium.com/@arnav_aggarwal)'s explanation to be the clearest. The following rules are applied:

1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument.
3. If a function is called as a method, such as `obj.method()` — `this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode (`'use strict'`), `this` will be `undefined` instead of the global object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

For an in-depth explanation, do check out his [article on Medium](https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3).

###### References

- https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3
- https://stackoverflow.com/a/3127440/1751946

### Explain how prototypal inheritance works

This is an extremely common JavaScript interview question. All JavaScript objects have a `prototype` property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's `prototype`, and the `prototype`'s `prototype` and so on, until it finds the property defined on one of the `prototype`s or until it reaches the end of the prototype chain. This behaviour simulates classical inheritance, but it is really more of [delegation than inheritance](https://davidwalsh.name/javascript-objects).

###### References

- https://www.quora.com/What-is-prototypal-inheritance/answer/Kyle-Simpson
- https://davidwalsh.name/javascript-objects

### What do you think of AMD vs CommonJS?

Both are ways to implement a module system, which was not natively present in JavaScript until ES2015 came along. CommonJS is synchronous while AMD (Asynchronous Module Definition) is obviously asynchronous. CommonJS is designed with server-side development in mind while AMD, with its support for asynchronous loading of modules, is more intended for browsers.

I find AMD syntax to be quite verbose and CommonJS is closer to the style you would write import statements in other languages. Most of the time, I find AMD unnecessary, because if you served all your JavaScript into one concatenated bundle file, you wouldn't benefit from the async loading properties. Also, CommonJS syntax is closer to Node style of writing modules and there is less context-switching overhead when switching between client side and server side JavaScript development.

I'm glad that with ES2015 modules, that has support for both synchronous and asynchronous loading, we can finally just stick to one approach. Although it hasn't been fully rolled out in browsers and in Node, we can always use transpilers to convert our code.

###### References

- https://auth0.com/blog/javascript-module-systems-showdown/
- https://stackoverflow.com/questions/16521471/relation-between-commonjs-amd-and-requirejs

### Explain why the following doesn't work as an IIFE: `function foo(){ }();`. What needs to be changed to properly make it an IIFE?

IIFE stands for Immediately Invoked Function Expressions. The JavaScript parser reads `function foo(){ }();` as `function foo(){ }` and `();`, where the former is a function declaration and the latter (a pair of brackets) is an attempt at calling a function but there is no name specified, hence it throws `Uncaught SyntaxError: Unexpected token )`.

Here are two ways to fix it that involves adding more brackets: `(function foo(){ })()` and `(function foo(){ }())`. These functions are not exposed in the global scope and you can even omit its name if you do not need to reference itself within the body.

###### References

- http://lucybain.com/blog/2014/immediately-invoked-function-expression/

### What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?

**Undeclared** variables are created when you assign to a value to an identifier that is not previously created using `var`, `let` or `const`. Undeclared variables will be defined globally, outside of the current scope. In strict mode, a `ReferenceError` will be thrown when you try to assign to an undeclared variable. Undeclared variables are bad just like how global variables are bad. Avoid them at all cost! To check for them, wrap its usage in a `try`/`catch` block.

```js
function foo() {
  x = 1;   // Throws a ReferenceError in strict mode
}

foo()
console.log(x) // 1
```

A variable that is `undefined` is a variable that has been declared, but not assigned a value. It is of type `undefined`. If a function does not return any value as the result of executing it is assigned to a variable, the variable also has the value of `undefined`. To check for it, compare using the strict equality (`===`) operator or `typeof` which will give the `'undefined'` string. Note that you should not be using the abstract equality operator to check, as it will also return `true` if the value is `null`.

```js
var foo;
console.log(foo); // undefined
console.log(foo === undefined); // true
console.log(typeof foo === 'undefined'); // true

console.log(foo == null); // true. Wrong, don't use this to check!

function bar() {}
var baz = bar();
console.log(baz); // undefined
```

A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from `undefined` in the sense that it has been explicitly assigned. To check for `null,` simply compare using the strict equality operator. Note that like the above, you should not be using the abstract equality operator (`==`) to check, as it will also return `true` if the value is `undefined`.

```js
var foo = null;
console.log(foo === null); // true

console.log(foo == undefined); // true. Wrong, don't use this to check!
```

As a personal habit, I never leave my variables undeclared or unassigned. I will explicitly assign `null` to them after declaring, if I don't intend to use it yet.

###### References

- https://stackoverflow.com/questions/15985875/effect-of-declared-and-undeclared-variables
- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/undefined

### What is a closure, and how/why would you use one?

A closure is the combination of a function and the lexical environment within which that function was declared. The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Closures are functions that have access to the outer (enclosing) function's variables—scope chain even after the outer function has returned.

**Why would you use one?**

- Data privacy / emulating private methods with closures. Commonly used in the [module pattern](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript).
- [Partial applications or currying](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8#.l4b6l1i3x).

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36

### What's a typical use case for anonymous functions?

They can be used in IIFEs to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope.

```js
(function() {
  // Some code here.
})();
```

As a callback that is used once and does not need to be used anywhere else. The code will seem more self-contained and readable when handlers are defined right inside the code calling them, rather than having to search elsewhere to find the function body.

```js
setTimeout(function () {
  console.log('Hello world!');
}, 1000);
```

Arguments to functional programming constructs or Lodash (similar to callbacks).

```js
const arr = [1, 2, 3];
const double = arr.map(function (el) {
  return el * 2;
});
console.log(double); // [2, 4, 6]
```

###### References

- https://www.quora.com/What-is-a-typical-usecase-for-anonymous-functions
- https://stackoverflow.com/questions/10273185/what-are-the-benefits-to-using-anonymous-functions-instead-of-named-functions-fo

### How do you organize your code? (module pattern, classical inheritance?)

In the past, I used Backbone for my models which encourages a more OOP approach, creating Backbone models and attaching methods to them.

The module pattern is still great, but these days, I use the Flux architecture based on React/Redux which encourages a single-directional functional programming approach instead. I would represent my app's models using plain objects and write utility pure functions to manipulate these objects. State is manipulated using actions and reducers like in any other Redux application.

I avoid using classical inheritance where possible. When and if I do, I stick to [these rules](https://medium.com/@dan_abramov/how-to-use-classes-and-sleep-at-night-9af8de78ccb4).

### What's the difference between host objects and native objects?

Native objects are objects that are part of the JavaScript language defined by the ECMAScript specification, such as `String`, `Math`, `RegExp`, `Object`, `Function`, etc.

Host objects are provided by the runtime environment (browser or Node), such as `window`, `XMLHTTPRequest`, etc.

###### References

- https://stackoverflow.com/questions/7614317/what-is-the-difference-between-native-objects-and-host-objects

### Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

This question is pretty vague. My best guess at its intention is that it is asking about constructors in JavaScript. Technically speaking, `function Person(){}` is just a normal function declaration. The convention is use PascalCase for functions that are intended to be used as constructors.

`var person = Person()` invokes the `Person` as a function, and not as a constructor. Invoking as such is a common mistake if it the function is intended to be used as a constructor. Typically, the constructor does not return anything, hence invoking the constructor like a normal function will return `undefined` and that gets assigned to the variable intended as the instance.

`var person = new Person()` creates an instance of the `Person` object using the `new` operator, which inherits from `Person.prototype`. An alternative would be to use `Object.create`, such as: `Object.create(Person.prototype)`.

```js
function Person(name) {
  this.name = name;
}

var person = Person('John');
console.log(person); // undefined
console.log(person.name); // Uncaught TypeError: Cannot read property 'name' of undefined

var person = new Person('John');
console.log(person); // Person { name: "John" }
console.log(person.name); // "john"
```

###### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new

### What's the difference between `.call` and `.apply`?

Both `.call` and `.apply` are used to invoke functions and the first parameter will be used as the value of `this` within the function. However, `.call` takes in a comma-separated arguments as the next arguments while `.apply` takes in an array of arguments as the next argument. An easy way to remember this is C for `call` and comma-separated and A for `apply` and array of arguments.

```js
function add(a, b) {
  return a + b;
}

console.log(add.call(null, 1, 2)) // 3
console.log(add.apply(null, [1, 2])) // 3
```

### Explain `Function.prototype.bind`.

Taken word-for-word from [MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind):

> The `bind()` method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

In my experience, it is most useful for binding the value of `this` in methods of classes that you want to pass into other functions. This is frequently done in React components.

###### References

- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind

### When would you use `document.write()`?

`document.write()` writes a string of text to a document stream opened by `document.open()`. When `document.write()` is executed after the page has loaded, it will call `document.open` which clears the whole document (`<head>` and `<body>` removed!) and replaces the contents with the given parameter value in string. Hence it is usually considered dangerous and prone to misuse.

There are some answers online that explain `document.write()` is being used in analytics code or [when you want to include styles that should only work if JavaScript is enabled](https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html). It is even being used in HTML5 boilerplate to [load scripts in parallel and preserve execution order](https://github.com/paulirish/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag)! However, I suspect those reasons might be outdated and in the modern day, they can be achieved without using `document.write()`. Please do correct me if I'm wrong about this.

###### References

- https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html
- https://github.com/h5bp/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag

### What's the difference between feature detection, feature inference, and using the UA string?

**Feature Detection**

Feature detection involves working out whether a browser supports a certain block of code, and running different code dependent on whether it does (or doesn't), so that the browser can always provide a working experience rather crashing/erroring in some browsers. For example:

```js
if ('geolocation' in navigator) {
  // Can use navigator.geolocation
} else {
  // Handle lack of feature
}
```

[Modernizr](https://modernizr.com/) is a great library to handle feature detection.

**Feature Inference**

Feature inference checks for a feature just like feature detection, but uses another function because it assumes it will also exist, e.g.:

```js
if (document.getElementsByTagName) {
    element = document.getElementById(id);
}
```

This is not really recommended. Feature detection is more foolproof.

**UA String**

This is a browser-reported string that allows the network protocol peers to identify the application type, operating system, software vendor or software version of the requesting software user agent. It can be accessed via `navigator.userAgent`. However, the string is tricky to parse and can be spoofed. For example, Chrome reports both as Chrome and Safari. So to detect Safari you have to check for the Safari string and the absence of the Chrome string. Avoid this method.

###### References

- https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection
- https://stackoverflow.com/questions/20104930/whats-the-difference-between-feature-detection-feature-inference-and-using-th
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Browser_detection_using_the_user_agent

### Explain Ajax in as much detail as possible.

Ajax (asynchronous JavaScript and XML") is a set of web development techniques using many web technologies on the client side to create asynchronous web applications. With Ajax, web applications can send data to and retrieve from a server asynchronously (in the background) without interfering with the display and behavior of the existing page. By decoupling the data interchange layer from the presentation layer, Ajax allows for web pages, and by extension web applications, to change content dynamically without the need to reload the entire page. In practice, modern implementations commonly substitute JSON for XML due to the advantages of being native to JavaScript.

The `XMLHttpRequest` API is frequently used for the asynchronous communication or these days, the `fetch` API.

###### References

- https://en.wikipedia.org/wiki/Ajax_(programming)
- https://developer.mozilla.org/en-US/docs/AJAX

### What are the advantages and disadvantages of using Ajax?

**Advantages**

- Better interactivity. New content from the server can be changed dynamically without the need to reload the entire page.
- Reduce connections to the server since scripts and stylesheets only have to be requested once.
- State can be maintained on a page. JavaScript variables and DOM state will persist because the main container page was not reloaded.
- Basically most of the advantages of an SPA.

**Disadvantages**

- Dynamic webpages are harder to bookmark.
- Does not work if JavaScript has been disabled in the browser.
- Some webcrawlers do not execute JavaScript and would not see content that has been loaded by JavaScript.
- Basically most of the disadvantages of an SPA.

### Explain how JSONP works (and how it's not really Ajax).

JSONP (JSON with Padding) is a method commonly used to bypass the cross-domain policies in web browsers because Ajax requests from the current page to a cross-origin domain is not allowed.

JSONP works by making a request to a cross-origin domain via a `<script>` tag and usually with a `callback` query parameter, for example: `https://example.com?callback=printData`. The server will then wrap the data within a function called `printData` and return it to the client.

```html
<!-- https://mydomain.com -->
<script>
function printData(data) {
  console.log(`My name is ${data.name}!`);
}
</script>

<script src="https://example.com?callback=printData"></script>
```

```js
// File loaded from https://example.com?callback=printData
printData({ name: 'Yang Shun' });
```

The client has to have the `printData` function in its global scope and the function will be executed by the client when the response from the cross-origin domain is received.

JSONP can be unsafe and has some security implications. As JSONP is really JavaScript, it can do everything else JavaScript can do, so you need to trust the provider of the JSONP data.

These days, [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) is the recommended approach and JSONP is seen as a hack.

###### References

- https://stackoverflow.com/a/2067584/1751946

### Have you ever used JavaScript templating? If so, what libraries have you used?

Yes. Handlebars, Underscore, Lodash, AngularJS and JSX. I disliked templating in AngularJS because it made heavy use of strings in the directives and typos would go uncaught. JSX is my new favourite as it is closer to JavaScript and there is barely and syntax to be learnt. Nowadays, you can even use ES2015 template string literals as a quick way for creating templates without relying on third-party code.

```js
const template = `<div>My name is: ${name}</div>`;
```

However, do beware of a potential XSS in the above approach as the contents are not escaped for you, unlike in templating libraries.

### Explain "hoisting".

Hoisting is a term used to explain the behavior of variable declarations in your code. Variables declared or initialized with the `var` keyword will have their declaration "hoisted" up to the top of the current scope. However, only the declaration is hoisted, the assignment (if there is one), will stay where it is. Let's explain with a few examples.

```js
// var declarations are hoisted.
console.log(foo); // undefined
var foo = 1;
console.log(foo); // 1

// let/const declarations are NOT hoisted.
console.log(bar); // ReferenceError: bar is not defined
let bar = 2;
console.log(bar); // 2
```

Function declarations have the body hoisted while the function expressions (written in the form of variable declarations) only has the variable declaration hoisted.

```js
// Function Declaration
console.log(foo); // [Function: foo]
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
console.log(foo); // [Function: foo]

// Function Expression
console.log(bar); // undefined
bar(); // Uncaught TypeError: bar is not a function
var bar = function() {
  console.log('BARRRR');
}
console.log(bar); // [Function: bar]
```

### Describe event bubbling.

When an event triggers on a DOM element, it will attempt to handle the event if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. This bubbling occurs up the element's ancestors all the way to the `document`. Event bubbling is the mechanism behind event delegation.

### What's the difference between an "attribute" and a "property"?

Attributes are defined on the HTML markup but properties are defined on the DOM. To illustrate the difference, imagine we have this text field in our HTML: `<input type="text" value="Hello">`.

```js
const input = document.querySelector('input');
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello
```

But after you change the value of the text field by adding "World!" to it, this becomes:

```js
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello World!
```

###### References

- https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html

### Why is extending built-in JavaScript objects not a good idea?

Extending a built-in/native JavaScript object means adding properties/functions to its `prototype`. While this may seem like a good idea at first, it is dangerous in practice. Imagine your code uses a few libraries that both extend the `Array.prototype` by adding the same `contains` method, the implementations will overwrite each other and your code will break if the behavior of these two methods are not the same.

The only time you may want to extend a native object is when you want to create a polyfill, essentially providing your own implementation for a method that is part of the JavaScript specification but might not exist in the user's browser due to it being an older browser.

###### References

- http://lucybain.com/blog/2014/js-extending-built-in-objects/

### Difference between document load event and document DOMContentLoaded event?

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.

`window`'s `load` event is only fired after the DOM and all dependent resources and assets have loaded.

###### References

- https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded
- https://developer.mozilla.org/en-US/docs/Web/Events/load

### What is the difference between `==` and `===`?

`==` is the abstract equality operator while `===` is the strict equality operator. The `==` operator will compare for equality after doing any necessary type conversions. The `===` operator will not do type conversion, so if two values are not the same type `===` will simply return `false`. When using `==`, funky things can happen, such as:

```js
1 == '1' // true
1 == [1] // true
1 == true // true
0 == '' // true
0 == '0' // true
0 == false // true
```

My advice is never to use the `==` operator, except for convenience when comparing against `null` or `undefined`, where `a == null` will return `true` if `a` is `null` or `undefined`.

```js
var a = null;
console.log(a == null); // true
console.log(a == undefined); // true
```

###### References

- https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons

### Explain the same-origin policy with regards to JavaScript.

The same-origin policy prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number. This policy prevents a malicious script on one page from obtaining access to sensitive data on another web page through that page's Document Object Model.

###### References

- https://en.wikipedia.org/wiki/Same-origin_policy

### Make this work:

```js
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```

```js
function duplicate(arr) {
  return arr.concat(arr);
}

duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```

### Why is it called a Ternary expression, what does the word "Ternary" indicate?

"Ternary" indicates three, and a ternary expression accepts three operands, the test condition, the "then" expression and the "else" expression. Ternary expressions are not specific to JavaScript and I'm not sure why it is even in this list.

###### References

- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Conditional_Operator

### What is `"use strict";`? What are the advantages and disadvantages to using it?

'use strict' is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt in to a restricted variant of JavaScript.

Advantages:

- Makes it impossible to accidentally create global variables.
- Makes assignments which would otherwise silently fail to throw an exception.
- Makes attempts to delete undeletable properties throw (where before the attempt would simply have no effect).
- Requires that function parameter names be unique.
- `this` is undefined in the global context.
- It catches some common coding bloopers, throwing exceptions.
- It disables features that are confusing or poorly thought out.

Disadvantages:

- Many missing features that some developers might be used to.
- No more access to `function.caller` and `function.arguments`.
- Concatenation of scripts written in different strict modes might cause issues.

Overall, I think the benefits outweigh the disadvantages, and I never had to rely on the features that strict mode blocks. I would recommend using strict mode.

###### References

- http://2ality.com/2011/10/strict-mode-hatred.html
- http://lucybain.com/blog/2014/js-use-strict/

### Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`.

Check out this version of FizzBuzz by [Paul Irish](https://gist.github.com/jaysonrowe/1592432#gistcomment-790724).

```js
for (let i = 1; i <= 100; i++) {
  let f = i % 3 == 0, b = i % 5 == 0;
  console.log(f ? (b ? 'FizzBuzz' : 'Fizz') : (b ? 'Buzz' : i));
}
```

I would not advise you to write the above during interviews though. Just stick with the long but clear approach. For more wacky versions of FizzBuzz, check out the reference link below.

###### References

- https://gist.github.com/jaysonrowe/1592432

### Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?

Every script has access to the global scope, and if everyone is using the global namespace to define their own variables, there will bound to be collisions. Use the module pattern (IIFEs) to encapsulate your variables within a local namespace.

### Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

The `load` event fires at the end of the document loading process. At this point, all of the objects in the document are in the DOM, and all the images, scripts, links and sub-frames have finished loading.

The DOM event `DOMContentLoaded` will fire after the DOM for the page has been constructed, but do not wait for other resources to finish loading. This is preferred in certain cases when you do not need the full page to be loaded before initializing.

TODO.

###### References

- https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers/onload

### Explain what a single page app is and how to make one SEO-friendly.

The below is taken from the awesome [Grab Front End Guide](https://github.com/grab/front-end-guide), which coincidentally, is written by me!

Web developers these days refer to the products they build as web apps, rather than websites. While there is no strict difference between the two terms, web apps tend to be highly interactive and dynamic, allowing the user to perform actions and receive a response for their action. Traditionally, the browser receives HTML from the server and renders it. When the user navigates to another URL, a full-page refresh is required and the server sends fresh new HTML for the new page. This is called server-side rendering.

However in modern SPAs, client-side rendering is used instead. The browser loads the initial page from the server, along with the scripts (frameworks, libraries, app code) and stylesheets required for the whole app. When the user navigates to other pages, a page refresh is not triggered. The URL of the page is updated via the [HTML5 History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API). New data required for the new page, usually in JSON format, is retrieved by the browser via [AJAX](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started) requests to the server. The SPA then dynamically updates the page with the data via JavaScript, which it has already downloaded in the initial page load. This model is similar to how native mobile apps work.

The benefits:

- The app feels more responsive and users do not see the flash between page navigations due to full-page refreshes.
- Fewer HTTP requests are made to the server, as the same assets do not have to be downloaded again for each page load.
- Clear separation of the concerns between the client and the server; you can easily build new clients for different platforms (e.g. mobile, chatbots, smart watches) without having to modify the server code. You can also modify the technology stack on the client and server independently, as long as the API contract is not broken.

The downsides:

- Heavier initial page load due to loading of framework, app code, and assets required for multiple pages.
- There's an additional step to be done on your server which is to configure it to route all requests to a single entry point and allow client-side routing to take over from there.
- SPAs are reliant on JavaScript to render content, but not all search engines execute JavaScript during crawling, and they may see empty content on your page. This inadvertently hurts the Search Engine Optimization (SEO) of your app. However, most of the time, when you are building apps, SEO is not the most important factor, as not all the content needs to be indexable by search engines. To overcome this, you can either server-side render your app or use services such as [Prerender](https://prerender.io/) to "render your javascript in a browser, save the static HTML, and return that to the crawlers".

###### References

- https://github.com/grab/front-end-guide#single-page-apps-spas
- http://stackoverflow.com/questions/21862054/single-page-app-advantages-and-disadvantages
- http://blog.isquaredsoftware.com/presentations/2016-10-revolution-of-web-dev/
- https://medium.freecodecamp.com/heres-why-client-side-rendering-won-46a349fadb52

### What is the extent of your experience with Promises and/or their polyfills?

Possess working knowledge of it. A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it's not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

Some common polyfills are `$.deferred`, Q and Bluebird but not all of them comply to the specification. ES2015 supports Promises out of the box and polyfills are typically not needed these days.

###### References

- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

### What are the pros and cons of using Promises instead of callbacks?

**Pros**

- Avoid callback hell which can be unreadable.
- Makes it easy to write sequential asynchronous code that is readable with `.then()`.
- Makes it easy to write parallel asynchronous code with `Promise.all()`.

**Cons**

- Slightly more complex code (debatable).
- In older browsers where ES2015 is not supported, you need to load a polyfill in order to use it.

### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

Some examples of languages that compile to JavaScript include CoffeeScript, Elm, ClojureScript, PureScript and TypeScript.

Advantages:

- Fixes some of the longstanding problems in JavaScript and discourages JavaScript anti-patterns.
- Enables you to write shorter code, by providing some syntactic sugar on top of JavaScript, which I think ES5 lacks, but ES2015 is awesome.
- Static types are awesome (in the case of TypeScript) for large projects that need to be maintained over time.

Disadvantages:

- Require a build/compile process as browsers only run JavaScript and your code will need to be compiled into JavaScript before being served to browsers.
- Debugging can be a pain if your source maps do not map nicely to your pre-compiled source.
- Most developers are not familiar with these languages and will need to learn it. There's a ramp up cost involved for your team if you use it for your projects.
- Smaller community (depends on the language), which means resources, tutorials, libraries and tooling would be harder to find.
- IDE/editor support might be lacking.
- These languages will always be behind the latest JavaScript standard.
- Developers should be cognizant of what their code is being compiled to — because that is what would actually be running, and that is what matters in the end.

Practically, ES2015 has vastly improved JavaScript and made it much nicer to write. I don't really see the need for CoffeeScript these days.

###### References

- https://softwareengineering.stackexchange.com/questions/72569/what-are-the-pros-and-cons-of-coffeescript

### What tools and techniques do you use for debugging JavaScript code?

- React and Redux
  - [React Devtools](https://github.com/facebook/react-devtools)
  - [Redux Devtools](https://github.com/gaearon/redux-devtools)
- JavaScript
  - [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d)
  - `debugger` statement
  - Good old `console.log` debugging

###### References

- https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d
- https://raygun.com/blog/javascript-debugging/

### What language constructions do you use for iterating over object properties and array items?

For objects:

- `for` loops - `for (var property in obj) { console.log(property); }`. However, this will also iterate through its inherited properties, and you will add an `obj.hasOwnProperty(property)` check before using it.
- `Object.keys()` - `Object.keys(obj).forEach(function (property) { ... })`. `Object.keys()` is a static method that will lists all enumerable properties of the object that you pass it.

For arrays:

- `for` loops - `for (var i = 0; i < arr.length; i++)`. The common pitfall here is that `var` is in the function scope and not the block scope and most of the time you would want block scoped iterator variable. ES2015 introduces `let` which has block scope and it is recommended to use that instead. So this becomes: `for (let i = 0; i < arr.length; i++)`.
- `forEach` - `arr.forEach(function (el, index) { ... })`. This construct can be more convenient at times because you do not have to use the `index` if all you need is the array elements. There are also the `every` and `some` methods which will allow you to terminate the iteration early.

Most of the time, I would prefer the `.forEach` method, but it really depends on what you are trying to do. `for` loops allow more flexibility, such as prematurely terminate the loop using `break` or incrementing the iterator more than once per loop.

### Explain the difference between mutable and immutable objects.

- What is an example of an immutable object in JavaScript?
- What are the pros and cons of immutability?
- How can you achieve immutability in your own code?

TODO

### Explain the difference between synchronous and asynchronous functions.

Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.

Asynchronous functions usually accept a callback as a parameter and execution continues on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to complete (in the case of browsers, the UI will freeze).

### What is event loop? What is the difference between call stack and task queue?

The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

If you haven't already checked out Philip Robert's [talk on the Event Loop](https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html), you should. It is one of the most viewed videos on JavaScript.

###### References

- https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html
- http://theproactiveprogrammer.com/javascript/the-javascript-event-loop-a-stack-and-a-queue/

### Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`

The former is a function declaration while the latter is a function expression. The key difference is that function declarations have its body hoisted but the bodies of function expressions are not (they have the same hoisting behaviour as variables). For more explanation on hoisting, refer to the question above on hoisting. If you try to invoke a function expression before it is defined, you will get an `Uncaught TypeError: XXX is not a function` error.

**Function Declaration**

```js
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
```

**Function Expression**

```js
foo(); // Uncaught TypeError: foo is not a function
var foo = function() {
  console.log('FOOOOO');
}
```

