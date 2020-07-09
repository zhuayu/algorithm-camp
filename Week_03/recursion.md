# 递归的实现、特性以及思维要点

为什么树的面试题解法一般都是递归？

1. 树的节点结构它数据结构的定义就是用递归的方式来进行的
1. 不仅是树的本身二叉树、搜索二叉树，在定义数据结构和算法特性的时候有重复性。


递归的本身是一个循环，只不过在循环体内调用自己来进行循环。

## 递归模版
递归模版主要有四个组成部分：

1. 递归终结条件 recursion terminator
1. 处理当前逻辑 process logic
1. 下探到下一层 drill down
1. 清理当前层（ 可选：释放内存）reverse the current level status if needed



```python
# Python
def recursion(level, param1, param2, ...): 
    # recursion terminator 
    if level > MAX_LEVEL: 
     process_result 
     return 
    # process logic in current level 
    process(level, data...) 
    # drill down 
    self.recursion(level + 1, p1, ...) 
    # reverse the current level status if needed
```
```java
// Java
public void recur(int level, int param) { 
  // terminator 
  if (level > MAX_LEVEL) { 
    // process result 
    return; 
  }
  // process current logic 
  process(level, param); 
  // drill down 
  recur( level: level + 1, newParam); 
  // restore current status 

}
```


## 思维要点

1. 不要人肉进行递归
1. 找到最近最简方法，将其拆解成可重复解决的问题
1. 数学归纳思维
