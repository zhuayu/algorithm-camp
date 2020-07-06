# 二叉树的前序遍历
> https://leetcode-cn.com/problems/binary-tree-preorder-traversal/

## 题目

给定一个二叉树，返回它的 前序 遍历。

示例:

```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 
输出: [1,2,3]
```

进阶: 递归算法很简单，你可以通过迭代算法完成吗？

## 思路

1. 递归

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
 * @return {number[]}
 */
var preorderTraversal = function(root) {
  const result = [];
  if(!root) return result;
  const recursiveFunc = node => {
    if(node.val) result.push(node.val)
    node.left && recursiveFunc(node.left)
    node.right && recursiveFunc(node.right)
  }
  recursiveFunc(root)
  return result
};
```