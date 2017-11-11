 Given an array of integers, return indices of the two numbers such that they add up to a specific target.

 You may assume that each input would have exactly one solution.

 Example:
 Given nums = [2, 7, 11, 15], target = 9,

 Because nums[0] + nums[1] = 2 + 7 = 9,
 return [0, 1].
 UPDATE (2016/2/13):
 The return format had been changed to zero-based indices. Please read the above updated description carefully.

 Hide Company Tags LinkedIn Uber Airbnb Facebook Amazon Microsoft Apple Yahoo Dropbox Bloomberg Yelp Adobe
 Hide Tags Array Hash Table
 Hide Similar Problems (M) 3Sum (M) 4Sum (M) Two Sum II - Input array is sorted (E) Two Sum III - Data structure design
```

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var hash = {};
    
    for(var i = 0; i < nums.length; i++) {
        var num = nums[i];
        if(hash[num] !== undefined) {
            return [hash[num], i]
        } else {
            hash[target - num] = i;
        }
    }
    
    return [];
}
```


# Same Tree
```
var isSameTree = function(p, q) {
    if(!p && !q)  return true
    else if ((p && !q) || (!p && q) || p.val !== q.val) return false
    else return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
};
```

# Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

//     1
//    / \
//   2   2
//  / \ / \
// 3  4 4  3
// But the following [1,2,2,null,3,null,3] is not:
//     1
//    / \
//   2   2
//    \   \
//    3    3
// Note:
// Bonus points if you could solve it both recursively and iteratively.

// Hide Company Tags LinkedIn Bloomberg Microsoft
// Hide Tags Tree Depth-first Search Breadth-first Search

```
var isSymmetric = function(root) {
    function isSymmetricNode(left, right) {
        if(!left && !right) {
            return true;
        }
        if((left && !right) || (!left && right)) {
            return false;
        }
        return (left.val == right.val)
            && isSymmetricNode(left.left, right.right)
            && isSymmetricNode(left.right, right.left);
    }
    if(root === null) {
        return true;
    }
    var left = root.left;
    var right = root.right;
    return isSymmetricNode(left, right);
};
```
# Binary Tree Level Order Traversal
```
var traversal = function(ret, root, depth) {
    if(root === null) {
        return;
    }
    if(!Array.isArray(ret[depth])) {
        ret[depth] = [];
    }
    ret[depth].push(root.val);
    traversal(ret, root.left, depth + 1);
    traversal(ret, root.right, depth + 1);
}

var levelOrder = function(root) {
    var ret = [];
    traversal(ret, root, 0);
    return ret;
};
```

# First non repeating char
```
function firstNonRepeatedCharacter(string) {
    var first;

    string.split('').some(function (character, index, obj) {
        if(obj.indexOf(character) === obj.lastIndexOf(character)) {
            first = character;
            return true;
        }

        return false;
    });

    return first;
}
```

# Generate random number between two numbers in JavaScript

```
function randomIntFromInterval(min,max)
{
    return Math.floor(Math.random()*(max-min+1)+min);
}
```


We are given 3 strings: str1, str2, and str3. Str3 is said to be a shuffle of str1 and str2 if it can be formed by interleaving the characters of str1 and str2 in a way that maintains the left to right ordering of the characters from each string. For example, given str1="abc" and str2="def", str3="dabecf" is a valid shuffle since it preserves the character ordering of the two strings. So, given these 3 strings write a function that detects whether str3 is a valid shuffle of str1 and str2.

```
function isShuffle(str1, str2, shuffle) {
  var pointer1 = str1.length - 1;
  var pointer2 = str2.length - 1;
  var shufflePointer = shuffle.length - 1;

  while (shufflePointer >= 0) {
    if (shuffle[shufflePointer] === str2[pointer2]) {
      pointer2--;
    } else if (shuffle[shufflePointer] === str1[pointer1]){
      pointer1--;
    } else {
      return false;
    }

    shufflePointer--;
  }
  return true;
}

```
## Stack & Queue
```
var Stack = function(){
  this.top = null;
  this.size = 0;
};

var Node = function(data){
  this.data = data;
  this.previous = null;
};

Stack.prototype.push = function(data) {
  var node = new Node(data);

  node.previous = this.top;
  this.top = node;
  this.size += 1;
  return this.top;
};

Stack.prototype.pop = function() {
  temp = this.top;
  this.top = this.top.previous;
  this.size -= 1;
  return temp;
};
```
```
var Queue = function() {
  this.first = null;
  this.size = 0;
};

var Node = function(data) {
  this.data = data;
  this.next = null;
};

Queue.prototype.enqueue = function(data) {
  var node = new Node(data);

  if (!this.first){
    this.first = node;
  } else {
    n = this.first;
    while (n.next) {
      n = n.next;
    }
    n.next = node;
  }

  this.size += 1;
  return node;
};

Queue.prototype.dequeue = function() {
  temp = this.first;
  this.first = this.first.next;
  this.size -= 1;
  return temp;
};
```

# prime
```
function(n) {
    if(n === 1) { return false;}
    else if(n == 2) { return true;}
    else if(n == 3) { return true;}
    else { 
        for(i=Math.floor(Math.sqrt(n));i>=2;i--){
            //console.log(i);//maybe another var in here? 
                if(n%i ==0 || n%2 ==0 || n%3 == 0) {return false;} 
        } 
        }
    return true;
};
```

# odd-occuring-element
```
module.exports = function (array) {
  return array.reduce(function (memo, number) {
    return memo ^ number;
  }, 0);
};
```
# Array from value
```
Array.from(Array(10).keys())
[...Array(10).keys()]
```

# missing-number
```
module.exports = function (array) {
  return ((array.length + 1) * (2 + array.length) / 2) - array.reduce(function (memo, number) {
    return memo + number;
  }, 0);
};
```

## matching node
```
/* global isMatchingNode */

// Make the function accept the node from the first tree and the second tree
// where we need to find the matching node
module.exports = function (node, tree) {
  // Easiest way to optimize this is to store the path from the node to the root
  // and then we can traverse back down the second tree following the same path
  var path  = [node],
  // Use the child variable to find the matching node in the second tree
      child = tree;

  // Loop through all the parent nodes, pushing it into the stack as the pathway
  while (node = node.parentNode) {
    path.push(node);
  }

  // Pop the last thing we pushed onto the path since it'll be the root node
  // E.g. It'll be the tree that we are passing in anyway
  path.pop();

  // Once the loop is done, we have the root node and can go back down the tree
  while (node = path.pop()) {
    for (var i = 0; i < child.childNodes.length; i++) {
      // Here we assume we have a function called `isMatchingNode` that returns
      // us a boolean in the case of two nodes matching each other
      if (isMatchingNode(node, child.childNodes[i])) {
        child = child.childNodes[i];
        break; // Break looping over more nodes
      }
    }
  }

  return child;
};
```

# big word
```

down vote
You can custom sort based on string length, and grab the first item:

longWords.sort(function(a, b) { 
    return b.length - a.length; 
});
```
