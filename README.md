# Interview-Question-answers
// Spiral output for array
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
