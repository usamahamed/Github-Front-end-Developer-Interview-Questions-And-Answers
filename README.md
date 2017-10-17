# Interview-Question-answers
 Spiral output for array
var m = [
  [0,  1,  2,  3,  4],
  [5,  6,  7,  8,  9],
  [10, 11, 12, 13, 14],
  [15, 16, 17, 18, 19]
];

var spiral = function (m) {
 // Put your code here
}; // Should be [0, 1, 2, 3, 4, 9, 14, 19, 18, 17, 16, 15, 10, 5, 6, 7, 8, 13, 12, 11]
```
var input = [[1,  2,   3,  4],
             [5,  6,   7,  8],
             [9,  10, 11, 12],
             [13, 14, 15, 16]];

var spiralTraversal = function(matriks){
  var result = [];
    var goAround = function(matrix) {
        if (matrix.length == 0) {
            return;
        }

        // right
        result = result.concat(matrix.shift());

        // down
        for (var j=1; j < matrix.length - 1; j++) {
            result.push(matrix[j].pop());
        }

        // bottom
        result = result.concat(matrix.pop().reverse());

        // up
        for (var k=matrix.length -2; k > 0; k--) {
            result.push(matrix[k].shift());
        }

        return goAround(matrix);
    };

    goAround(matriks);

    return result;
};
var result = spiralTraversal(input);

console.log('result', result);
```
=====================================================================================
// Sort array with semver-rules
var arr = [ "1.0.5", "2.5.0", "0.12.0", "1", "1.23.45", "1.4.50", "1.2.3.4.5.6.7"];

function semverSor() {
  // put your code here
}

semverSor(arr); // Like [ "0.12", "1.0.5", "1.2.3.4.5.6.7", "1.23.45", "1.4.50", "2.5.0" ]
```
function cmpVersions (a, b) {
    var i, diff;
    var regExStrip0 = /(\.0+)+$/;
    var segmentsA = a.replace(regExStrip0, '').split('.');
    var segmentsB = b.replace(regExStrip0, '').split('.');
    var l = Math.min(segmentsA.length, segmentsB.length);

    for (i = 0; i < l; i++) {
        diff = parseInt(segmentsA[i], 10) - parseInt(segmentsB[i], 10);
        if (diff) {
            return diff;
        }
    }
    return segmentsA.length - segmentsB.length;
}
```
=====================================================================================
 Implement deepClone ( withour recursive links and functions
 simpliest , suppose is JSON.parse(JSON.stringify(m)) but we need real code =)
 ```
 function copy(aObject) {
  var bObject, v, k;
  bObject = Array.isArray(aObject) ? [] : {};
  for (k in aObject) {
    v = aObject[k];
    bObject[k] = (typeof v === "object") ? copy(v) : v;
  }
  return bObject;
}
 ```
 =====================================================================================
  Implement bind(func, context). Make polyfill .bind(context)
```
var slice = Array.prototype.slice;

function bind (fn, context /*, ...args */) {
  var args = slice.call(arguments, 2);

  return function () {
    return fn.apply(context, args.concat(slice.call(arguments)));
  };
};
```
 =====================================================================================

// We have next stub
// Fill blank methods to describe algorithms for servicing multistory building with your elevator
// You have only low-leve intarface (HardwareElevator) with three states - stoppes, move up, move down
// Every floor has two buttons up/down
// Inside cabin there are only buttons with numbers
```
DIRECTION_DOWN = -1
DIRECTION_NONE = 0
DIRECTION_UP = 1

function HardwareElevator(){};
HardwareElevator.prototype = {
    moveUp:function(){console.log('moving up');},
    moveDown:function(){console.log('moving down');},
    stopAndOpenDoors:function(){console.log('stopping and opening doors');},
    getCurrentFloor:function(){console.log('getting current floor');},
    getCurrentDirection:function(){console.log('getting current drection');}
}

function Elevator() {
    this.hw = new HardwareElevator();
    this.hw.addEventListener("doorsClosed", _bind(this.onDoorsClosed, this));
    this.hw.addEventListener("beforeFloor", _bind(this.onBeforeFloor, this));
}
Elevator.prototype = {
    onDoorsClosed: function(floor) {
      // put your code here
    },
    onBeforeFloor: function(floor, direction) {
      // put your code here
    },
    floorButtonPressed: function(floor, direction) {
      // put your code here
    },
    cabinButtonPressed: function(floor) {
      // put your code here
    }
}
```
solution
```
var DIRECTION_DOWN = -1
var DIRECTION_NONE = 0
var DIRECTION_UP = 1
 
function HardwareElevator(){};
HardwareElevator.prototype = {
    moveUp:function(){console.log('moving up');},
    moveDown:function(){console.log('moving down');},
    stopAndOpenDoors:function(){console.log('stopping and opening doors');},
    getCurrentFloor:function(){console.log('getting current floor');},
    getCurrentDirection:function(){console.log('getting current drection');}
}
 
function Elevator() {
    this.hw = new HardwareElevator();
    this.hw.addEventListener("doorsClosed", _.bind(this.onDoorsClosed, this));
    this.hw.addEventListener("beforeFloor", _.bind(this.onBeforeFloor, this));
   
    // array of { floor: int, dir: int } objects
    this.currentStack = [];
    this.nextStack = [];
   
    this.direction = 0;
}
Elevator.prototype = {
    onDoorsClosed: function(floor) {
        if (this.destinations.length) {
            var destination = this.destinations.pop();
            if (destination.floor === floor) {
                this.hw.stopAndOpenDoors();
            } else if  (destination.floor > floor) {
                this.hw.moveUp();
            } else {
                this.hw.moveDown();
            }
        }
    },
    onBeforeFloor: function(floor, direction) {
        if (this.destinations[0] !== undefined
            && this.destinations[0] === floor
        ) {
            this.hw.stopAndOpenDoors();
        }
    },
    floorButtonPressed: function(floor, direction) {
        var currentFloor = this.hw.getCurrentFloor();
        var currentDirection = this.hw.getCurrentDirection();
        var directionCorresponds = currentDirection === direction || currentDirection = 0;
               
    },
    cabinButtonPressed: function(floor) {
        var currentFloor = this.hw.getCurrentFloor();
       
        if (currentFloor === floor) {
            this.hw.stopAndOpenDoors();
        }
       
        this.destinations.push({
            dir: currentFloor > floor ?  -1 : 1,
            floor: floor
        });
    }
}
```
 =====================================================================================
//We want to write calculations using functions and get the results. Let's have a look at some examples:
// seven(times(five())); // must return 35
// four(plus(nine())); // must return 13
// eight(minus(three())); // must return 5
// six(dividedBy(two())); // must return 3
//Requirements:
//There must be a function for each number from 0 ("zero") to 9 ("nine")
//There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy (divided_by in Ruby)
//Each calculation consist of exactly one operation and two numbers
//The most outer function represents the left operand, the most inner function represents the right operand
```
function recur(n, op) { return (op) ? op.call(op, n) : n; }
function zero(op)     { return recur(0, op); }
function one(op)      { return recur(1, op); }
function two(op)      { return recur(2, op); }
function three(op)    { return recur(3, op); }
function four(op)     { return recur(4, op); }
function five(op)     { return recur(5, op); }
function six(op)      { return recur(6, op); }
function seven(op)    { return recur(7, op); }
function eight(op)    { return recur(8, op); }
function nine(op)     { return recur(9, op); }

function plus(num) {
    return function(res) {
        return res + num;
    };
}
function minus(num) {
    return function(res) {
        return res - num;
    };
}
function times(num) {
    return function(res) {
        return res * num;
    };
}
function dividedBy(num) {
    return function(res) {
        return res / num;
    };
}
```
 =====================================================================================
// implement simple module system with injection system like in angular
```
var service = function() {
    return { name: 'Service' };
}
var router = function() {
    return { name: 'Router' };
}
var doSomething = function(service, router, other) {
    var s = service();
    var r = router();
};
```
=====================================================================================
// Output?
var f = (function f(){ return "1"; }, function g(){ return 2; })();
typeof f;
```
number
```
=====================================================================================
// Game where everyone win. Output?
<button id="btn-0">Button 1!</button>
<button id="btn-1">Button 2!</button>
<button id="btn-2">Button 3!</button>
<script type="text/javascript">
    var prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
    for (var btnNum = 0; btnNum < prizes.length; btnNum++) {
        // for each of our buttons, when the user clicks it...
        document.getElementById('btn-' + btnNum).onclick = function() {
            // tell her what she's won!
            alert(prizes[btnNum]);
        };
    }
</script>
     ```
     undefine
     use let or wrap in function scope
     ```
=====================================================================================
Create compose function
 const compose = (f1, f2) => value => f1( f2(value) )
 list of functions can has any length
 for zero-length list it should return () => undefined
 compose(fn, fn1, fn2, fn3) 
     
    ``` 
    const compose = (...fns) =>fns.reverse().reduce((prevFn, nextFn) =>value => nextFn(prevFn(value)),value => value);
```const compose2 = (f, g) => (...args) => f(g(...args))```
```const compose = (...fns) => fns.reduce(compose2);```
```const pipe = (...fns) => fns.reduceRight(compose2);```
     
 =====================================================================================
	    
 Implement .map  using .reduce for iteration ( for arrays )
 ```
 module.exports = function arrayMap(arr, fn) {
    'use strict';
    return arr.reduce(function (prev, current) {
        return prev.concat(fn(current));
    }, []);
};
 ```
 =====================================================================================
     
 / Suppose findData is a function that takes a query object and returns a promise for the result of the query. 
// Suppose also that someRandomArrayOfQueries is an array of query objects. 
// Explain what would be printed by the following code and why
function runMultipleQueries(queries) {
 var results = [];
 queries.forEach(doQuery);
 return results;

 function doQuery(query) {
   findData(query)
   .then(results.push.bind(results));
 } 
}
function log(value) {
 console.log(value);
}
runMultipleQueries(someRandomArrayOfQueries).forEach(log);

- doQuery is executed at some point in the future. The array however is returned and logged immediately. Therefore the array is still empty and nothing is being logged. To fix this runMultipleQueries needs to return a promise as well. That could e.g. look like this.
```
function runMultipleQueries(queries) {
 return new Promise(function(resolve, reject) {
   var results = [];
   queries.forEach(doQuery);

   function doQuery(query) {
     findData(query)
     .then(function(result) {
         results.push(result);
         if(results.length === queries.length) resolve(results);
     }, reject);
   }
 });
}
```
 =====================================================================================
describe('Step 5', function() {
  it('add(2,8)(5).value() => 15', function() {
    add(2,8)(5).value()
      .should.be.exactly(15).and.be.a.Number;
  });
  it('add(3, 3, 5)(4)(3, 2).value() => 20', function() {
    add(3, 3, 5)(4)(3, 2).value()
      .should.be.exactly(20).and.be.a.Number;
  });
});
```

```

 =====================================================================================
Given two identical DOM trees (not the same one), and a node from one of them find the node in the other one.
```
function indexOf(arrLike, target) {
    return Array.prototype.indexOf.call(arrLike, target);
}

// Given a node and a tree, extract the nodes path 
function getPath(root, target) {
    var current = target;
    var path = [];
    while(current !== root) {
        path.unshift(indexOf(current.parentNode.childNodes, current));
        current = current.parentNode;
    }
    return path;
}

// Given a tree and a path, let's locate a node
function locateNodeFromPath(root, path) {
    var current = root;
    for(var i = 0, len = path.length; i < len; i++) {
        current = current.childNodes[path[i]];
    }
    return current;
}

function getDoppleganger(rootA, rootB, target) {
    return locateNodeFromPath(rootB, getPath(rootA, target));
}
```
=====================================================================================
// What is the difference between these four promises?
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```
1 and 4 are the sync and what it's recommended to be used most of the time
2 and 3 are the async and are not that common/useful. Some would even consider it an error
// 1
doSomething().then(function () {
    return doSomethingElse();
}).then(finalHandler);

/*
doSomething
|-------------------|
                    doSomethingElse(undefined)
                    |-------------------|
                                        finalHandler(resultOfDoSomethingElse)
                                        |-------------------|
*/

// 2
doSomething().then(function () {
    doSomethingElse();
}).then(finalHandler);

/*
doSomething
|-------------------|
                    doSomethingElse(undefined)
                    |-------------------|
                    finalHandler(undefined)
                    |-------------------|
*/

// 3
doSomething().then(doSomethingElse())
.then(finalHandler);

/*
doSomething
|-------------------|
doSomethingElse(undefined)
|-------------------------------------|
                    finalHandler(resultOfDoSomething)
                    |-------------------|
*/
                        
// 4
doSomething().then(doSomethingElse)
.then(finalHandler);

/*
doSomething
|-------------------|
                    doSomethingElse(resultOfDoSomething)
                    |-------------------|
                                        finalHandler(resultOfDoSomethingElse)
                                        |-------------------|
*/                                          
```
=====================================================================================
```
Promise.resolve('foo').then(Promise.resolve('bar')).then(function (result) {
  console.log(result);  // This prints out 'foo'!
});
```
 The reason this happens is because when you pass then() a non-function (such as a promise), it actually interprets
 it is then(null), which causes the previous promise's result to fall through. You can test this yourself:
```
Promise.resolve('foo').then(null).then(function (result) {
  console.log(result);
});
```
 This actually circles back to the previous point about promises vs promise factories. In short, you CAN pass a promise
 directly into a then() method, but it won't do what you think it's doing. then() is supposed to take a function,
 so most likely you meant to do:
```
Promise.resolve('foo').then(function () {
    return Promise.resolve('bar');
}).then(function (result) {
    console.log(result);    // This will print out 'bar' as expected.
});
```
// So just remind yourself: always pass a function into then()!

/*
 * Advanced mistake #2: catch() isn't exactly like then(null, ...)
*/
```
// These two snippets are equivalent:
somePromise.catch(function (err) {
   // handle error 
});

somePromise().then(null, function (err) {
   // handle error 
});
```
// However, that doesn't mean that the following two snippets are equivalent:
```
somePromise().then(function () {
    return someOtherPromise();
}).catch(function (err) {
    // handle error
});

somePromise().then(function () {
    return someOtherPromise();
}, function (err) {
   // handle error 
});
```
// As it turns out, when you use the then(resolveHandler, rejectHandler) format, the rejectHandler 
// WON'T ACTUALLY CATCH AN ERROR IF IT'S THROWN BY THE resolveHandler ITSELF.
// For this reason, make it a habit to NEVER use the second argument to then(), and to ALWAYS PREFER catch().
// The exception is when writing asynch (Mocha, for instance) tests, where you might write a test to ensure that an error is thrown.

/*
 * Advanced mistake #3: promises vs promise factories
*/
// Let's say you want to execute a series of promises one after the other, in a sequence.
// That is, your want something like Promise.all(), but which doesn't execute promises in parallel.
// You might naively write something like this:
```
function executeSequentially(promises) {
    var result = Promise.resolve();
    promises.forEach(function (promise) {
        result = result.then(promise);
    });
    return result;
}
```
// Unfortunately, this will not work the way you intended. The promises you pass in to executeSequentially() will STILL 
// execute in parallel. The reason this happens is that you don't want to operate over an array of promises at all.
// Per the promise spec, as soon as a promise is created, it begins executing. So what you really want is an array of PROMISE FACTORIES:
```
function executeSequentially(promiseFactories) {
    var result = Promise.resolve();
    promiseFactories.forEach(function (promiseFactory) {
        result = result.then(promiseFactory);
    });
    return result;
}
```
// Why does this work?? It works because a promise factory doesn't create the promise until it's asked to. It works the same way
// as a then function - in fact, it's the same thing!
// If you look at the executeSequentially() function above, and then image myPromiseFactory being substituted inside of result.then(...),
// then hopefully a light bulb will click in your brain and you will have achieved promise enlightenment!
```
function myPromiseFactory() {
    return somethingThatCreatesAPromise();
}
```
/*
 * Advanced mistake #4: What if I want the result of two promises?
*/
// Often times, one promise will depend on another, but we'll want the output of both promises. For instance:
```
getUserByName('emily').then(function (user) {
    return getUserAccountById(user.id);
}).then(function (userAccount) {
    // dangit, I need the 'user' object too!!
});
```
// Wanting to be good JS devs and avoid the pyramid of doom, we might just store the 'user' object in a higher-scoped variable:
```
var user;
getUserByName('emily').then(function (result) {
    user = result;
    return getUserAccountById(user.id);
}).then(function (userAccount) {
    // okay, I have both the 'user' and the 'userAccount'
});
```
// This works, but it is a bit klunky. Recommended strategy: just let go of your preconceptions and embrace the pyramid:
```
getUserByName('emily').then(function (user) {
    return getUserAccountById(user.id).then(function (userAccount) {
    // okay, I have both the 'user' and the 'userAccount'
    });
});
```
// ...at least temporarily. If the indentation ever becomes an issue, just do what JS devs have done since the beginning - 
// extract the function into a named function:
```
function onGetUserAndUserAccount(user, userAccount) {
    return doSomething(user, userAccount);
}

function onGetUser(user) {
    return getUserAccountById(user.id).then(function (userAccount) {
        return onGetUserAndUserAccount(user, userAccount);
    });
}

getUserByName('emily')
    .then(onGetUser)
    .then(function () {
    // At this point, doSomething() is done and we are back to indentation 0
});
```
/* 
 * Rookie Mistake #3: Forgetting to add .catch()
*/
```
somePromise().then(function (){
    return anotherPromise();
}).then(function () {
    return yetAnotherPromise();
}).catch(console.log.bind(console)); // <-- this is badass
```
/* 
 * Rookie Mistake #4: Using side effects instead of returning
*/
```
somePromise().then(function (){
    someOtherPromise();
}).then(function (){
    // Gee, I hope someOtherPromise() has resolved!
    // Spoiler alert: It hasn't.
});
```

/* 
 * The ONE WEIRD TRICK that, once you understand it, will prevent all of the errors discussed so far.
 * The magic of promises is that they give us back our precious return and throw. But what does this 
 * look like in practice?
 * Every promise gives you a then() method (or catch(), which is just sugar for then(null, ...)).
 * Here we are inside a then() function:
*/
```
somePromise().then(function () {
   // I'm inside a then() function! 
});
```
/*
 * What can we do here? There are three things:
    1. return another promise
    2. return a synchronous value (or undefined)
    3. throw a synchronous error
*/

/*
 * 1. Return another promise
*/
// A common pattern, aka 'composing promises'
```
getUserByName('emily').then(function (user) {
    return getUserAccountById(user.id);     // Notice the return here. If we didn't say return, then the getUserAccountById() would actually be a side effect, and the next function would receive undefined instead of the userAccount.
}).then(function (userAccount) {
    // I got a user account!
});
```
/*
 * 2. Return a synchronous value (or undefined)
*/
// Returning undefined is often a mistake, but returning a synchronous value is actually an awesome way to 
// convert synchronous code into promisey code. For instance, let's say we have an in-memory cache of users. We can do:
```
getUserByName('emily').then(function (user) {
    if (inMemoryCache[user.id]) {
        return inMemoryCache[user.id];      // returning a synchronous value!
    }
    return getUserAccountById(user.id);     // returning a promise!
}).then(function (userAccount) {
    // I got a user account!
});
```
// The second function doesn't care whether the userAccount was fetchedd synchronously or asynchronously, 
// and the first function is free to return either a synchronous or asynchronous value.
// Unfortunately, there's the inconvenient fact that non-returning functions in javascript technically return undefined,
// which means it's easy to accidentally introduce side effects when you meant to return something.
// For this reason, you should make it a personal habit to ALWAYS RETURN OR THROW from inside a then() function.

/*
 * 3. Throw a synchronous error.
*/
// Let's say we want to throw a synchronous error in case the user is logged out. It's quite easy:
```
getUserByName('emily').then(function (user) {
    if (user.isLoggedOut()) {
        throw new Error('user logged out!');    // throwing a synchronous error!
    }
    if (inMemoryCache[user.id]) {
        return inMemoryCache[user.id];      // returning a synchronous value!
    }
    return getUserAccountById(user.id);     // returning a promise!
}).then(function (userAccount) {
    // I got a user account!
}).catch(function (err) {
    // Boo, I got an error!
});
```
// Our catch() will receive a synch error if the user is logged out, and it will receive an asynch error if ANY OF THE PROMISES ARE REJECTED.
// Again, the function doesn't care whether the error it gets is synch or asynch.
// This is especially useful bc it can help identify coding errors during dev. For instance, if at any point inside of a then() function we do
// a JSON.parse(), it might throw a synch error if the JSON is invalid. With callbacks, that error would get swallowed, but with promises,
// we can simply handle it inside our catch() function.


/*
 * Advanced mistake #1: Not knowing about Promise.resolve().
*/
// Promises are very useful for wrapping synch code as async code. However, if you find yourself typing this a lot:
```
new Promise(function (resolve, reject) {
    resolve(someSynchValue);
}).then(/* ... */);
// You can express this more succinctly using Promise.resolve():
Promise.resolve(someSynchValue).then(/* ... */);
```
// Just remember: any code that might throw synchronously is a good candidate for a nearly-impossible-to-debug swalled error somewhere down the line.
// But if you wrap everything in Promise.resolve(), then you can always be sure to catch() it later.
// A good habit to get into is to begin all of your promise-returning API methods like this:
```
function somePromiseAPI() {
    return Promise.resolve().then(function () {
        doSomethingThatMayThrow();
        return 'foo';
    }).then(/* ... */);
}
```
 Promise.reject() will return a promise that is immediately rejected.
Promise.reject(new Error(console.log('some awful error')));

=====================================================================================

<div id="selectio">Select me!</div>
 create js code ( via native js ) which on click at div will select all text inside
 note - just check range/selection api
```
<script type="text/javascript">
    function selectText(containerid) {
        if (document.selection) {
            var range = document.body.createTextRange();
            range.moveToElementText(document.getElementById(containerid));
            range.select();
        } else if (window.getSelection) {
            var range = document.createRange();
            range.selectNode(document.getElementById(containerid));
            window.getSelection().addRange(range);
        }
    }
</script>
```
=====================================================================================
Given an array of numbers, you should find the number which occurs an odd number of times within the array. 
```
function findOddAmount(numbers) {
	return numbers.reduce((p, n) => p ^ n);
}
```
=====================================================================================
what do you like in lodash/underscore?


=====================================================================================
what is the output?
```
function say(a) {
  alert(a);
}
say(1);
setTimeout(say(2), 5000);
setTimeout(function() {
  say(3);
}, 1000);
setTimeout(say, 2000, 4);
```
1 2 3 4
=====================================================================================

// The following recursive code will cause a stack overflow if the array list is too large.
// How can you fix this and still retain the recursive pattern?
```
var list = readHugeList();
var nextListItem = function() {
  var item = list.pop();
  if (item) {
    // process the list item...
    nextListItem();
  }
};
```
The potential stack overflow can be avoided by modifying the nextListItem function as follows:
```
var list = readHugeList();

var nextListItem = function() {
    var item = list.pop();

    if (item) {
        // process the list item...
        setTimeout( nextListItem, 0);
    }
};
```
The stack overflow is eliminated because the event loop handles the recursion, not the call stack. When nextListItem runs, if item is not null, the timeout function (nextListItem) is pushed to the event queue and the function exits, thereby leaving the call stack clear. When the event queue runs its timed-out event, the next item is processed and a timer is set to again invoke nextListItem. Accordingly, the method is processed from start to finish without a direct recursive call, so the call stack remains clear, regardless of the number of iterations
=====================================================================================
// What is the output
```
(function() {
  console.log(1);
  setTimeout(() => console.log(2), 1000);
  setTimeout(() => console.log(3), 0);
  Promise.resolve(true).then(() => console.log(4));
  console.log(5);
})();
```
1 5 4 0 2
Cycle 1:

`setInterval` is scheduled as task
`setTimeout 1` is scheduled as task
in `Promise.resolve 1` both `then`s are scheduled as microtasks
the stack is empty, microtasks are run
Task queue: setInterval, setTimeout 1

Cycle 2:

the microtask queue is empty, `setInteval`'s handler can be run, another `setInterval` is scheduled as a task, right behind setTimeout 1

=====================================================================================
// What is the output?
```
var a = 1;
function b() {
  a = 10;
  return;
  function a() {
  }
}
b();
console.log(a);
```
because of hoisting of function decleration
https://stackoverflow.com/questions/28060101/how-the-below-javascript-scope-works
=====================================================================================
// What is the output?
```
var a = {};
var b = { key: 'b' };
var c = { key: 'c' };

a[b] = 123;
a[c] = 456;
```
456 because b or c converted to string not object
https://stackoverflow.com/questions/29285901/why-ac-override-ab

 What is the output?
```
console.log("1" + 2); //12
console.log(2 + "1");  //21
console.log(1 + 2 + 3 + 4 + "5");  //105
```
// What is the output?
```
(function {
  alert(inner);  //undefine
  inner();       // type error inner is not function
  var inner = function() {
    alert('inner');
  }
})();
```

// What is the output?
```
(function() {
  f();
  f = function() {
    console.log(1);
  }
})();

function f() {
  console.log(2)
}
f();
```
print 2 and after that print 1

// number / undefined / function / Error ?
```var f = function g(){ return 23; };
typeof g();  //ReferenceError: g is not defined
 ```
 // what is x ?
```var y = 1, x = y = typeof x;
x; // number
```

// Output?
```var x = [typeof x, typeof y][1];
typeof typeof x;
```
typeof typeof x is "string". The quickest logic to this is to observe that typeof x always yields a string, no matter what x is. typeof typeof x thus always results in the string "string". As a side note, [typeof x, typeof y][1] can be simplified to typeof y after evaluation.

// Output?  Just be attentive
```(function(foo){
  return typeof foo.bar;
})({ foo: { bar: 1 } });
```
The above expression results in the string "undefined". The confusion factor is easier to eliminate by rewriting multiple times. First, we pull out the anonymous function's only argument:

```var baz = { foo: { bar: 1 } }; 
(function(foo){ 
  return typeof foo.bar; 
})(baz); 
```
Next, we eliminate the function by inlining it:
```
var baz = { foo: { bar: 1 } }; 
var foo = baz; 
typeof foo.bar; 
```
Finally, by substitution we remove the intermediate variable foo as well:
```
var baz = { foo: { bar: 1 } }; 
typeof baz.bar; 
```
At this point it becomes clear that the property bar is not defined for baz; it is defined for baz.foo. typeof baz.bar therefore yields "undefined".

// Output
```
(function() {
    logMe();
    var logMe = function() {
        console.log('Jesus, George, it was a wonder I was even born.');
    };
    logMe();

    function logMe() {
        console.log('Great Scott!');
    }
    logMe();
})();
```
print Great Scott!  Jesus, George, it was a wonder I was even born. Jesus, George, it was a wonder I was even born.

// result?
```new String('Hello') === 'Hello'  // false
```
Two String objects will always be unequal to each other. Note that JavaScript has string primitive values as well as a String constructor to create wrapper objects. All object equality comparisons (especially with ===) are carried out as a test for reference equality. References to two different objects will of course never be equal to each other.

So "hello" === "hello" will be true because those are string primitives.

// result?
```"This is a string" instanceof String; false
```
// output ?
```var a = 1;
var b = function() {
 a = 10;
 return a;
 function a() {
   a = 5;
  }
};
console.log(b(), a);  //print 10 1
```
// result?
```function f(){ return f; }
new f() instanceof f;
```
new f() instanceof f yields false. To understand why, it must first be known what new f() yields. The new operator creates a new object and calls the constructor function with this new object as its current context object. In other words, within the constructor, this points to the new object that is currently being created. After calling the constructor, the default semantics of the new operator is to yield said new object, even if the constructor returns some value.

// output?
```var text = 'outside';
function logIt(){
    console.log(text);
    var text = 'inside';
};
logIt();
```
In JavaScript, variables are "hoisted" to the top of the function. That is, unlike some other languages (such as C), a variable declared within a function is within scope throughout the function. So the compiler sees your function like this:
```
function logIt(){
    var text;
    console.log(text);
    text = 'inside';
} // <-- no semicolon after a function declaration
```
// output? ( nb: answer depends on environment / browser )
```
(function() {
 var a = 'initial';
  if(a) {
    function f() { console.log("1"); };
  } else {
    function f() { console.log("2"); };
  }
  f();
})();  // log 1
```
// output?
```(function() {
 var a = 0;
  f();
  if( a ) {
    function f() { console.log("1"); };
  } else {
    function f() { console.log("2"); };
  }
})();		//Uncaught TypeError: f is not a function

```
// What does the following code do? And why? ( quirks )
```falseStr = "false";
if(true){
  var falseStr;
  if(falseStr){
   console.log("false" == true);
   console.log("false" == false);
  }
}
```
http://www.technofattie.com/2014/09/03/the-best-javascript-interview-question.html

how to check if something is object?
// NB: asker should keep in mind:
// 1) typeof null => 'object'
// 2) Object.create(null) instanseof Object => false
// 3) typeof function() {} => 'function' , but it's still object

https://stackoverflow.com/questions/8511281/check-if-a-value-is-an-object-in-javascript


