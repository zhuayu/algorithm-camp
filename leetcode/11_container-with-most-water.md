# 盛最多水的容器
> https://leetcode-cn.com/problems/container-with-most-water/

## 题目

给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器，且 n 的值至少为 2。

## 思路

1. 暴力破解，双循环把每一种情况都算出来，获取最大值。公示：S = ( j - i ) * Math.min(ai, aj) , 时间复杂度 O(n^2)。
2. 两边收敛，两边谁的值小就往里面挪动，期待出现更大的值。因为木桶效应是取短木，不断的把短的木板抽掉。

## 执行

方法 二：两边收敛

```javascript
const maxArea = function(nums) {
  let max = 0;
  for (let i = 0, j = nums.length - 1; i < j; nums[i] > nums[j] ? j-- : i ++) {
    let area = (j - i) * Math.min(nums[j], nums[i]);
    max = Math.max(max, area);
  }
  return max;
};
```