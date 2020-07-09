# 二叉树的最大深度
> https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/

## 题目

给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
给定二叉树 [3,9,20,null,null,15,7]，

```
    3
   / \
  9  20
    /  \
   15   7
```

返回它的最大深度 3 。

## 思路

1. 递归把层数传递下去迭加，刷新最大值

## 执行

方法一：递归叠加层数，取最大值

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
 * @return {number}
 */
var maxDepth = function(root) {
  let maxdeep = 0;
  let recursive = (node, deep) => {
    if(!node) return maxdeep
    maxdeep = Math.max(deep, maxdeep);
    if(node.left) recursive(node.left, deep + 1, maxdeep)
    if(node.right) recursive(node.right, deep + 1, maxdeep)
  }
  recursive(root, 1)
  return maxdeep;
};
```