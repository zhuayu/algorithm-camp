# N叉树的层序遍历
> https://leetcode-cn.com/problems/n-ary-tree-level-order-traversal

给定一个 N 叉树，返回其节点值的层序遍历。 (即从左到右，逐层遍历)。

例如，给定一个 3叉树 :

![3叉树](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png)

返回其层序遍历:

```
[
     [1],
     [3,2,4],
     [5,6]
]
```

说明:

- 树的深度不会超过 1000。
- 树的节点总数不会超过 5000。

## 思路

1. 递归中把层级带下去

## 执行

方法一：递归层级

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
 * @return {number[][]}
 */
var levelOrder = function(root) {
  let result = [];
  if(!root) return result
  const recursiveFunc = (node, index) => {
    result[index] ? result[index].push(node.val) : result[index] = [node.val];
    if(node.children.length) {
      node.children.forEach(data => recursiveFunc(data, index + 1));
    }
  }
  recursiveFunc(root, 0);
  return result
};
```