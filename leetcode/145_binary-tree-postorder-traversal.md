# 二叉树的后序遍历
> https://leetcode-cn.com/problems/binary-tree-postorder-traversal/

## 题目

给定一个二叉树，返回它的 后序 遍历。

示例:

```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]
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
var postorderTraversal = function(root) {
      let result = [];
    if(!root) return result
    const recursiveFunc = node => {
      node.left && recursiveFunc(node.left)
      node.right && recursiveFunc(node.right)
      result.push(node.val);
    }
    recursiveFunc(root);
    return result;
};
```