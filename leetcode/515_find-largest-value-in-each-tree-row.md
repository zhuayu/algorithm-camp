# 在每个树行中找最大值
> https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/

## 题目

您需要在二叉树的每一行中找到最大的值。

示例：

```
输入: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

输出: [1, 3, 9]
```

## 思路

1. 广度搜索，然后取每一层最大值

## 执行

方法一：广度搜索

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
var largestValues = function(root) {
  let result = [], queue = [root];
  if(!root) return result;
  while(queue.length > 0) {
    let max = -Infinity, n = queue.length;
    for(let i = 0; i < n; i ++) {
      let node = queue.pop();
      max = Math.max(max, node.val);
      if(node.left) queue.unshift(node.left)
      if(node.right) queue.unshift(node.right)
    }
    result.push(max);
  }
  return result;
};
```
