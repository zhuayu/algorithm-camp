# 字母异位词分组
> https://leetcode-cn.com/problems/group-anagrams/

## 题目

给定一个字符串数组，将字母异位词组合在一起。（字母异位词指字母相同，但排列不同的字符串）

示例:

```
输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

说明：

- 所有输入均为小写字母。
- 不考虑答案输出的顺序。

## 思路

1. 暴力循环，用一个判断是否异词的函数遍历所有组合判断
2. 哈希表，把每一项进行排序然后作为 key 然后值为 value

## 执行

方法二：哈希表

```javascript
var groupAnagrams = function(strs) {
   var obj = {};
   strs.forEach((d, i) => {
      let key = d.split('').sort().join('');
      if(obj[key]) {
        obj[key].push(d);
      }else{
        obj[key] = [d];
      }
   })
   return Object.values(obj);
};
```


