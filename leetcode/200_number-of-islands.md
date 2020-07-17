# 岛屿数量
> https://leetcode-cn.com/problems/number-of-islands/

## 题目

给你一个由 '1'（陆地）和 '0'（水）组成的的二维网格，请你计算网格中岛屿的数量。

岛屿总是被水包围，并且每座岛屿只能由水平方向或竖直方向上相邻的陆地连接形成。

此外，你可以假设该网格的四条边均被水包围。

示例 1:

```
输入:
[
['1','1','1','1','0'],
['1','1','0','1','0'],
['1','1','0','0','0'],
['0','0','0','0','0']
]
输出: 1
```

示例 2:

```
输入:
[
['1','1','0','0','0'],
['1','1','0','0','0'],
['0','0','1','0','0'],
['0','0','0','1','1']
]
输出: 3
解释: 每座岛屿只能由水平和/或竖直方向上相邻的陆地连接而成。
```

## 思路

1. 双层遍历，然后深度优先把岛屿附近的陆地设置为 0 

## 执行

方法一：深度搜索把陆地附近移为平地

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */

var numIslands = function(grid) {
  const removeIsland = (i , j, grid) => {
    if(i < 0 || i > grid.length - 1 || j < 0 || j > grid[i].length - 1 || grid[i][j] == 0) return
    grid[i][j] = 0;
    removeIsland(i, j + 1, grid);
    removeIsland(i, j - 1, grid);
    removeIsland(i + 1, j, grid);
    removeIsland(i - 1, j, grid);
  }

  let count = 0;
  if(!grid.length) return count;
  for(let i = 0; i <= grid.length - 1; i ++) {
    for(let j = 0; j <= grid[i].length - 1; j ++) {
      if(grid[i][j] == 1) {
        removeIsland(i, j, grid);
        count ++
      }
    }
  }
  return count
};
```