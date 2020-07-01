# 剑指 Offer 40. 最小的k个数
> https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/submissions/

## 题目

输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

示例 1：

```
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
```

示例 2：

```
输入：arr = [0,1,2,1], k = 1
输出：[0]
```

限制：

- 0 <= k <= arr.length <= 10000
- 0 <= arr[i] <= 10000

## 思路

1. sort 排序，然后截取前 k 个。O(NlogN)
2. 堆，O(Nlogk)
3. 快速排序

## 执行

方法一：排序截取

```
var getLeastNumbers = function(arr, k) {
  return arr.sort((a,b) => a - b).splice(0,k)
};
```