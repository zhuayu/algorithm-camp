# 多数元素
> https://leetcode-cn.com/problems/majority-element/

## 题目

给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

示例 1:

```
输入: [3,2,3]
输出: 3
```

示例 2:

```
输入: [2,2,1,1,1,2,2]
输出: 2
```

## 思路

1. 放到映射里面，然后取出最大值

## 执行

方法一：放到映射，取最大值

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  let obj = {};
  nums.forEach(d => obj[d] ? obj[d] ++ : obj[d] = 1);
  let maxTotal = 0;
  let maxNumber = 0;
  for(key in obj) {
    if(obj[key] > maxTotal) {
      maxTotal = obj[key];
      maxNumber = key
    }
  }
  return maxNumber
};
```