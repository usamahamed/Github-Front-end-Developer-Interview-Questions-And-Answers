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
