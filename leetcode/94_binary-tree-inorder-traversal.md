# 二叉树的中序遍历

## 题目

给定一个二叉树，返回它的中序 遍历。

示例:

```
输入: [1,null,2,3]
   1
    \
     2
    /
   3

输出: [1,3,2]
```

## 思路

1. 左中右遍历

## 执行

方法 一：左中右

> 注意考虑 [] 的情况

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
 * @return {number[]}
 */

var inorderTraversal = function(root) {
  var result = [];
  var degui = function(node) {
    if(node.left) {
      degui(node.left)
    }
    result.push(node.val)
    if(node.right) {
      degui(node.right)
    }
  }
  root && degui(root);
  return result
};
```