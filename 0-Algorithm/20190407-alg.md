# Algorithm: 102. Binary Tree Level Order Traversal

## Code

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[][]}
 */
var levelOrder = function(root) {
    // Edge case: empty node
    if(!root) return [];
    var result = [], queue = [];
    queue.push(root);
    while(queue.length){
        var current_level = [], current_level_size = queue.length;
        for(var i=0;i<current_level_size;i++){
            var node = queue.shift();
            current_level.push(node.val);
            if(node.left) queue.push(node.left);
            if(node.right) queue.push(node.right);
        }
        result.push(current_level);
    }
    return result;
};
```