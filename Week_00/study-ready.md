# 训练准备

## 训练环境设置

- 浏览器和搜索引擎：Google（良好的上网习惯）
- 终端：Termianl
  - Mac: iTerm2 + zsh (oh my zsh) 
  - Windows: Microsoft new terminal: (https://github.com/microsoft/terminal)
- 编辑器：VSCode / LeetCode plugin / [themes](https://vscodethemes.com/)

## Code Style

搜索查看各家互联网公司规范

- Google code style
- Facebook
- Airbnb

## LeetCode

注册中国站、国际站 LeetCode

- leetcode-cn.com 中国站做题、看题解
- leetcode.com 国际站看高票答案

## 指法和小操作

搜索 vscode 使用技巧

- command + left/right 行头行尾
- option + left/right 单词头尾切分
- shift + command + right 选中整行
- fn + delete 删除光标右边
- option + delete 删除单词



## 自顶向下的编程方式

自顶向下的编程方式来自于《clean code》，用 newspaper metaphor 一样的形式。现代代码写出来的方式应该类似于报纸的方式，头版头条在前面，后面的才是细节。关键的函数在上面，其他私有的函数和一些细节逻辑的子函数就往文件或者这个类下面放。

```java
class Solution {
  public boolean isPalindrame(String s) {
    // 高层次（主干）逻辑
    // 1. filter out munber & clar；
    // 2. reverse and compare
    String filteredS = _filterNonNumberAndChar(s);
    return _reverseString(filteredS).equalsIgnoreCase(filteredS);
  }

  private String _reverseString(String s) {
    return new StringBuilder(s).reverse().toString();
  }

  private String _filterNonNumberAndChar(Stiing s) {
    return s.replaceAll("[^A-Za-z0-9]", "");
  }
}
```

参考地址：
- https://markhneedham.com/blog/2008/09/15/clean-code-book-review/
- https://leetcode-cn.com/problems/valid-palindrome/