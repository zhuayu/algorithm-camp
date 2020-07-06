# N叉树的后序遍历
> https://leetcode-cn.com/problems/n-ary-tree-postorder-traversal/

## 题目

给定一个 N 叉树，返回其节点值的后序遍历。

例如，给定一个 3叉树 :

![3叉树](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png)

返回其后序遍历: [5,6,3,2,4,1].

说明: 递归法很简单，你可以使用迭代法完成此题吗?


## 思路

1. 递归

## 执行

方法一：递归

```javascript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */

/**
 * @param {Node} root
 * @return {number[]}
 */
var postorder = function(root) {
    let result = [];
    if(!root) return result
    const recursive = node => {
      node.children.forEach(data => recursive(data));
      result.push(node.val);
    }
    recursive(root);
    return result;
};
```