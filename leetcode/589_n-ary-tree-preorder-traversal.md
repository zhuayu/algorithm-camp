# N叉树的前序遍历

## 题目

给定一个 N 叉树，返回其节点值的前序遍历。

例如，给定一个 3叉树 :


![3叉树](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png)

返回其前序遍历: [1,3,5,6,2,4]。


说明: 递归法很简单，你可以使用迭代法完成此题吗?


## 思路

1. 递归

## 执行

方法一：递归

```
/**
 * // Definition for a Node.
 * function Node(val, children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */

/**
 * @param {Node} root
 * @return {number[]}
 */
var preorder = function(root) {
    let result = [];
    if(!root) return result;
    let recover = function(node) {
      result.push(node.val);
      if(node.children.length) {
        node.children.forEach(itemNode => recover(itemNode))
      }
    }
    recover(root);
    return result
};
```