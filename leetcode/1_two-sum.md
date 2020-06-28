# 两数之和
> https://leetcode-cn.com/problems/two-sum

## 题目

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

## 思路

1. 暴力破解，双循环判断 O(n^2)
2. 空间换时间，字典下标法 O(n)

## 执行

方法一：暴力破解

```javascript
const twoSum = function(nums, target) {
  let result = [];
  for (let i = 0; i <= nums.length - 1; i ++ ) {
    for(let j = i + 1; j <= nums.length - 1; j ++ ) {
      if(nums[i] + nums[j] === target) {
        result = [i, j]
      }
    }
  }
  return result
};
```

方法二：空间换时间，字典下标法

```javascript
const twoSum = function(nums, target) {
  let result = [];
  let object = {};
  for (let i = 0; i <= nums.length - 1; i ++ ) {
    object[nums[i]] = i 
  }

  for (let i = 0; i <= nums.length - 1; i ++ ) {
    const num = target - nums[i];
    if(object[nums]) {
      result = [i, object[nums]]
    }
  }
  return result
};
```

> 有问题，[3, 3] 有重复的情况搞不定，字典没唯一。