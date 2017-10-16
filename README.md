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
https://github.com/Exictos-DCS/watch-your-language/blob/master/callbacks-and-promises.md
```
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

