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
  let obj = {};
  for (let i = 0; i <= strs.length - 1; i ++) {
    let str = strs[i].split('').sort().join('');
    if(obj[str]) {
      obj[str].push(i)
    }else{
      obj[str] = [i]
    }
  }
  return Object.values(obj).map( data => {
    return data.map(i => strs[i])
  })
};


var groupAnagrams = function(strs) {
  let map = new Map();
  for(let i = 0; i <= strs.length - 1; i ++) {
    let sortStr = strs[i].split('').sort().join('');
    let sortStrValue = map.get(sortStr)
    if(!sortStrValue) {
      map.set(sortStr,[i])
    }else {
      sortStrValue.push(i);
      map.set(sortStr, sortStrValue)
    }
  }

  let mapValues = map.values();
  let result = [];
  for (let values of mapValues) {
   let tmpValues = [];
   for(let value of values) {
     tmpValues.push(strs[value])
   }
   result.push(tmpValues)
  }
  return result
};
```


