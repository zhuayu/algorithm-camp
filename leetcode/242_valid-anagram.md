# 有效的字母异位词
> https://leetcode-cn.com/problems/valid-anagram/description/

## 题目

给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。**(字母出现的次数一样，顺序可以不一样)**

示例 1:

```
输入: s = "anagram", t = "nagaram"
输出: true
```

示例 2:

```
输入: s = "rat", t = "car"
输出: false
```

说明:
你可以假设字符串只包含小写字母。

进阶:
如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？

## 思路

1. 用 hash map 来存储每个单词和它对应的频次，然后对比两个 str 的属性和值都为 0。
2. 用 hash map 来存储每个单词和它对应的频次，开始 str 加一，后面的 str 减一，判断是否所有 value 都为 0 。

## 执行

方法 二：map 加减一

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */

var mapFun = function(map, key, type = 1) {
  let value = map.get(key);
  if(!value) {
    map.set(key, type === 1 ? 1 : -1 );
  } else {
    map.set(key, type === 1 ? ++value : --value );
  }
}

var isAnagram = function(s, t) {
  const slength = s.length;
  const tlength = t.length;
  if (slength !== t.length) { return false }
  const anagramMap = new Map();
  for (let i = 0; i <= slength -1; i ++ ) {
    let skey = s.charAt(i);
    let tkey = t.charAt(i);
    mapFun(anagramMap, skey);
    mapFun(anagramMap, tkey, 2);
  }
  let result = true;
  for (let [key, value] of anagramMap) {
    if(value !== 0) {
      result = false;
    }
  }
  return result
};
```