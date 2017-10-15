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
var spiralTraversal = function(matriks){
  var result = [];
    var goAround = function(matrix) {
        var len = matrix[0].length;
        if (len === 1) {
            result.concat(matrix[0]);
            return result;
        }
        if (len === 2) {
            result.concat(matrix[0]);
            result.push(matrix[1][1], matrix[1][0]);
            return result;
        }
        if (len > 2) {
            // right
            result.concat(matrix[0]);
            // down
            for (var j=1; j < matrix.length - 1; j++) {
                result.push(matrix[j][matrix.length -1]);
            }
            // left
            for (var l=matrix.length - 2; l > 0; l--) {
                result.push(matrix[matrix.length - 1][l]);
            }
            // up
            for (var k=matrix.length -2; k > 0; k--) {
                result.push(matrix[k][0]);
            }
        }
        // reset matrix for next loop
        var temp = matrix.slice();
        temp.shift();
        temp.pop();
        for (var i=0; i < temp.length - 1; i++) {
            temp[i] = temp[i].slice(1,-1);
        }
        goAround(temp);
    };
    goAround(matriks);  
};
```
=============================================================================================================================
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
=============================================================================================================================
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
 ============================================================================================================================
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
 ============================================================================================================================

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
 ============================================================================================================================
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
 ============================================================================================================================
// implement simple module system with injection system like in angular
