# 有效的完全平方数
> https://leetcode-cn.com/problems/valid-perfect-square/

## 题目

给定一个正整数 num，编写一个函数，如果 num 是一个完全平方数，则返回 True，否则返回 False。

说明：不要使用任何内置的库函数，如  sqrt。

示例 1：

```
输入：16
输出：True
```

示例 2：

```
输入：14
输出：False
```

## 思路

1. 二分查找

## 执行

方法一：二分查找

```
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function(num) {
  let [L, M, R] = [0, null, num];
  while(L <= R) {
    M = Math.floor((L + R)/2);
    if( M ** 2 === num) return true;
    else if( M ** 2 > num) R = M - 1;
    else if( M ** 2 < num) L = M + 1;
  }
  return false;
};
```

