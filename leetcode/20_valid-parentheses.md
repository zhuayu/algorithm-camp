# 有效的括号
> https://leetcode-cn.com/problems/valid-parentheses/

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:
```
输入: "()"
输出: true
```

示例 2:
```
输入: "()[]{}"
输出: true
```

示例 3:
```
输入: "(]"
输出: false
```

示例 4:
```
输入: "([)]"
输出: false
```

示例 5:
```
输入: "{[]}"
输出: true
```

## 思路

1. 使用栈，把左边的符号对应的压入栈中，如果是右边符号就取出栈的内容，看看是否对应。

## 执行

方法一：栈

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  let obj = {
    '(': ')',
    '{': '}',
    '[': ']'
  }
  let arr = [];
  if(s.length % 2) return false;
  for(let i = 0; i <= s.length - 1; i ++) {
    let str = s[i];
    if(obj[str]) {
      arr.push(obj[str])
    }else{
      let lastStr = arr.pop();
      if(lastStr !== str) {
        return false;
      }
    }
  }
  return arr.length === 0;
};
```
