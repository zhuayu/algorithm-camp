# 括号生成
> https://leetcode-cn.com/problems/generate-parentheses/

数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

示例：

```
输入：n = 3
输出：[
       "((()))",
       "(()())",
       "(())()",
       "()(())",
       "()()()"
     ]
```

## 思路

1. 递归添加左右括号，然后筛选左右数量为 n 的。

## 执行

方法一：递归添加括号筛选

```
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
  const recursive = (left, right, n , str, result) => {
    if(left === n && right === n) return result.push(str);
    if(left > right) recursive(left, right + 1, n, str + ')', result)
    if(left <= n) recursive(left + 1, right, n, str + '(', result);
    return result
  }
  return recursive(0, 0, n, '',[])
};
```
