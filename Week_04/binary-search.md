# 二分查找的实现、特性及实战题目解析

## 二分查找的前提
- 目标函数单调性(单调递增或者递减) 
- 存在上下界(bounded)
- 能够通过索引访问(index accessible)
> 单调性、上下界、索引


二分查找指的是在有序的里面进行查找（无序只能从头到尾遍历），因为是有序的，所以能通过判断它的某些特征排除掉前半部分或者后半部分。所以必须是单调的，可以单调递增，也可以单调递减。

存在上下界，否则它的空间可能是无穷大，就没法往中间扩展。

可以通过索引访问，所以如果是单链表，即使是有序的，也不太容易。

## 代码模版
左右界分别是 0 和数组长度减 1 ，也就是左右的下标值。while left 小于等于 right，然后得到中间值 mid 。判断 mid 是否等于 target ，如果是就返回。

假设数组是升序排列，如果 target 大于 array[mid] 的话，说明在右侧。继续向右查找，所以 left 就把左界向右界移动，变成 mid + 1 。否则就向左侧进行移动，右界变成 mid - 1。

```java
left, right = 0, len(array) - 1 
   while left <= right:
     mid = (left + right) / 2
     if array[mid] == target:
       # find the target!!
       break or return result
     elif array[mid] < target:
       left = mid + 1
     else:
       right = mid - 1
```

## 事例
在递增数组里 [10, 14, 19, 26, 27, 31, 33, 35, 42, 44] ，查找:31 。

如果用二分查找的方法，首先取中间值 27 ，31 和 27 进行对比大于 27 所以在右侧，排除前半部分从后半部分进行查找。然后继续找后半部分的中间值 35，31 比 35 小，说明在左侧，排除右半部分。以此类推，最后的找到 31 。


## 参考链接

- [二分查找代码模板](https://shimo.im/docs/xvIIfeEzWYEUdBPD/)
- [Fast InvSqrt() 扩展阅读](https://www.beyond3d.com/content/articles/8/)

## 实战题目

- [x 的平方根](https://leetcode-cn.com/problems/sqrtx/)（字节跳动、微软、亚马逊在半年内面试中考过）
- [有效的完全平方数](https://leetcode-cn.com/problems/valid-perfect-square/)（亚马逊在半年内面试中考过）

## 课后作业

- [搜索旋转排序数组](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)（Facebook、字节跳动、亚马逊在半年内面试常考）
- [搜索二维矩阵](https://leetcode-cn.com/problems/search-a-2d-matrix/)（亚马逊、微软、Facebook 在半年内面试中考过）
- [寻找旋转排序数组中的最小值](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)（亚马逊、微软、字节跳动在半年内面试中考过）
- 使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方说明：同学们可以将自己的思路、代码写在学习总结中


# 二分查找的实现、特性及实战题目解析

## 二分查找的前提
- 目标函数单调性(单调递增或者递减) 
- 存在上下界(bounded)
- 能够通过索引访问(index accessible)
> 单调性、上下界、索引


二分查找指的是在有序的里面进行查找（无序只能从头到尾遍历），因为是有序的，所以能通过判断它的某些特征排除掉前半部分或者后半部分。所以必须是单调的，可以单调递增，也可以单调递减。

存在上下界，否则它的空间可能是无穷大，就没法往中间扩展。

可以通过索引访问，所以如果是单链表，即使是有序的，也不太容易。

## 代码模版
左右界分别是 0 和数组长度减 1 ，也就是左右的下标值。while left 小于等于 right，然后得到中间值 mid 。判断 mid 是否等于 target ，如果是就返回。

假设数组是升序排列，如果 target 大于 array[mid] 的话，说明在右侧。继续向右查找，所以 left 就把左界向右界移动，变成 mid + 1 。否则就向左侧进行移动，右界变成 mid - 1。

```java
left, right = 0, len(array) - 1 
   while left <= right:
     mid = (left + right) / 2
     if array[mid] == target:
       # find the target!!
       break or return result
     elif array[mid] < target:
       left = mid + 1
     else:
       right = mid - 1
```


## 事例
在递增数组里 [10, 14, 19, 26, 27, 31, 33, 35, 42, 44] ，查找:31 。

如果用二分查找的方法，首先取中间值 27 ，31 和 27 进行对比大于 27 所以在右侧，排除前半部分从后半部分进行查找。然后继续找后半部分的中间值 35，31 比 35 小，说明在左侧，排除右半部分。以此类推，最后的找到 31 。




## 参考链接

- [二分查找代码模板](https://shimo.im/docs/xvIIfeEzWYEUdBPD/)
- [Fast InvSqrt() 扩展阅读](https://www.beyond3d.com/content/articles/8/)

## 实战题目

- [x 的平方根](https://leetcode-cn.com/problems/sqrtx/)（字节跳动、微软、亚马逊在半年内面试中考过）
- [有效的完全平方数](https://leetcode-cn.com/problems/valid-perfect-square/)（亚马逊在半年内面试中考过）

## 课后作业

- [搜索旋转排序数组](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)（Facebook、字节跳动、亚马逊在半年内面试常考）
- [搜索二维矩阵](https://leetcode-cn.com/problems/search-a-2d-matrix/)（亚马逊、微软、Facebook 在半年内面试中考过）
- [寻找旋转排序数组中的最小值](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)（亚马逊、微软、字节跳动在半年内面试中考过）
- 使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方说明：同学们可以将自己的思路、代码写在学习总结中

