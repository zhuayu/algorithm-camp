## 爬楼梯
> https://leetcode-cn.com/problems/climbing-stairs/

## 题目

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

示例 2：

```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

## 思路

开始没有思路，人脑列出来列到头疼，后来找找规律，发现 f(n) = f(n -1) + f(n -2) 。
想了一个解释的思路，由于我们跨最后一步的时候可以跨出 1 步 或者 2 步，假设 n 为 6 的时候。

- 如果最后一次是 1 步，那么它的可能性就是 f(5) 的每一种可能性后面多一步，其值为 f(5) 。
- 如果最后一次是 2 步，那么它的可能性就是 f(4) 的每一种可能性后面多两步，其值为 f(4) 。

所以 f(n) = f(n -1) + f(n -2) ，是一个 Fibonacci 函数。

1. 递归
2. 缓存叠加

## 执行

方法 一 ：递归 ( 复杂度太高，超出 LeetCode 时间限制 O(2^n))

```javascript
const climbStairs = function(n) {
  if( n <= 1) {
    return 1
  }

  if( n <= 2) {
    return 2
  }

  return climbStairs(n - 1) + climbStairs(n - 2)
};
```

方法 二：缓存叠加

```javascript
const climbStairs = function(n) {
  if(n === 1) { return 1 }
  if(n === 2) { return 2 }

  let f1 = 1, f2 = 2, f3 = 3;
  for (let i = 0; i <= n - 3; i ++) {
    f3 = f2 + f1;
    f1 = f2
    f2 = f3
  }
  return f3
};
```

