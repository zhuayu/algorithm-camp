# 搜索插入位置
> https://leetcode-cn.com/problems/search-insert-position/

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

示例 1:

```
输入: [1,3,5,6], 5
输出: 2
```

示例 2:
```
输入: [1,3,5,6], 2
输出: 1
```
示例 3:
```
输入: [1,3,5,6], 7
输出: 4
```
示例 4:
```
输入: [1,3,5,6], 0
输出: 0
```

## 思路 

1. 二分查找

## 执行

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
  let [L, M, R] = [0, null, nums.length - 1];
  while( L <= R) {
    let M = Math.floor((L + R)/2);
    console.log(L, M, R)
    if(nums[M] >= target) {
      R = M - 1;
    }else {
      L = M + 1;
    }
  }
  return L
};
```