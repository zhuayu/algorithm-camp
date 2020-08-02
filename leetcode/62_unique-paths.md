# 不同路径
https://leetcode-cn.com/problems/unique-paths/

## 题目

一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

问总共有多少条不同的路径？

例如，上图是一个7 x 3 的网格。有多少可能的路径？

![不同路径](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png)

示例 1:

```
输入: m = 3, n = 2
输出: 3
解释:
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向右 -> 向下
2. 向右 -> 向下 -> 向右
3. 向下 -> 向右 -> 向右
```

示例 2:

```
输入: m = 7, n = 3
输出: 28
```

提示：

- 1 <= m, n <= 100
- 题目数据保证答案小于等于 2 * 10 ^ 9

## 思路

1.  当前数等于左边 + 上边的数

## 执行

方法一：当前数等于左边 + 上边的数

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
//opt[i + 1][j] + opt[i][j + 1]
var uniquePaths = function(m, n) {
  let dp = []; 
  for(let i = 0; i <= m - 1; i ++) {
    if(!dp[i]) dp[i] = [];
    for(let j = 0; j <= n - 1; j ++) {
      // 第一行都为 1
      if(j === 0) dp[i][j] = 1;
      // 第一列都为 1
      else if(i === 0) dp[i][j] = 1;
      // 本格 = 左边 + 上边
      else {
        let L = dp[i - 1] ? dp[i - 1][j] : 0;
        let T = dp[i][j - 1] || 0;
        dp[i][j] = L + T;
      }
    }
  }

  return dp[m - 1][n - 1]
};
```