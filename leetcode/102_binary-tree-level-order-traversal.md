# 二叉树的层序遍历
> https://leetcode-cn.com/problems/binary-tree-level-order-traversal/

## 题目

给你一个二叉树，请你返回其按 层序遍历 得到的节点值。 （即逐层地，从左到右访问所有节点）。

```
示例：
二叉树：[3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [9,20],
  [15,7]
]
```

## 思路

1. 递归
2. 广度优先

## 执行

方法一：递归

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
  let recursion = (node, level ,result) => {
    if(!node) return result
    result[level] ?result[level].push(node.val) : result[level] = [node.val];
    if(node.left) recursion(node.left, level + 1, result);
    if(node.right) recursion(node.right, level + 1, result);
    return result
  }
  return recursion(root, 0, [])
};
```

方法二：广度优先

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
  let result = [], queue = [root];
  while(queue.length > 0) {
    let level = [], n = queue.length;
    for(let i = 0; i < n; i ++) {
      let node = queue.pop();
      level.push(node.val);
      if(node.left) queue.unshift(node.left);
      if(node.right) queue.unshift(node.right);
    }
    result.push(level)
  }
  return result
};
```