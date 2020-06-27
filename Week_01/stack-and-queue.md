# 栈和队列的实现与特性

## 栈和队列
- 栈可以想象成一个先入后出的容器结构，先进来的元素会叠在一起，不能从下面抽出。
- 队列可以想象成一个先进先出的排队场景，先进来的先出去，依次排队。

**Stack & Queue 关键点**

- Stack：先入后出；添加、删除皆为 O(1)，查询为 O(n)
- Queue：先入先出；添加、删除皆为 O(1)，查询为 O(n) 
- Deque：双端可进出，添加、删除皆为 O(1)，查询为 O(n) 

> 查询都为 O(n) 因为在栈或者队列中，元素都没有顺序可言，需要全部遍历一次。

**Deque：Double-End Queue 双端队列**

可以理解为一个 Stack 和 Queue 的结合体，它的头和尾都可以进行元素的出和入。

## Java Stack Queue 源码

TBD

## 参考链接

- [Java 的 PriorityQueue 文档](http://docs.oracle.com/javase/10/docs/api/java/util/PriorityQueue.html)
- [Java 的 Stack 源码](http://developer.classpath.org/doc/java/util/Stack-source.html)
- [Java 的 Queue 源码](http://fuseyism.com/classpath/doc/java/util/Queue-source.html)
- [Python 的 heapq](http://docs.python.org/2/library/heapq.html)
- [高性能的 container 库](http://docs.python.org/2/library/collections.html)
