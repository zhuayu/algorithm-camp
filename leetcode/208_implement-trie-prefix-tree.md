# 实现 Trie (前缀树)
> https://leetcode-cn.com/problems/implement-trie-prefix-tree/

## 题目

实现一个 Trie (前缀树)，包含 insert, search, 和 startsWith 这三个操作。

示例:

```
Trie trie = new Trie();

trie.insert("apple");
trie.search("apple");   // 返回 true
trie.search("app");     // 返回 false
trie.startsWith("app"); // 返回 true
trie.insert("app");   
trie.search("app");     // 返回 true
说明:

你可以假设所有的输入都是由小写字母 a-z 构成的。
保证所有输入均为非空字符串。
```

## 思路

1. 把每个字母变成一个对象，下一个字母是上一个字母的属性。并在最后一个字母上添加结束属性。

## 执行

方法 一：

```javascript
class Trie {
  constructor() {
    this.root = {}
  }
  insert(word) {
    let node = this.root
    for (const c of word) {
      if (!node[c]) node[c] = {}
      node = node[c]
    }
    node.isEnd = true;
  }
  traverse(word) {
    let node = this.root
    for (const c of word) {
      node = node[c]
      if (!node) return false
    }
    return node
  }
  search(word) {
    const node = this.traverse(word)
    return node && !!node.isEnd
  }
  startsWith(prefix) {
    return !!this.traverse(prefix)
  }
}
```