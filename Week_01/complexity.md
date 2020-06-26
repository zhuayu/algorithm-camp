# 复杂度分析

## 时间复杂度
时间复杂度用 Big O notation 表示，常用的有以下：

- O(1): Constant Complexity 常数复杂度
- O(n): Linear Complexity 线性时间复杂度 
- O(n^2): N square Complexity 平方
- O(n^3): N cubic Complexity 立方
- O(log n): Logarithmic Complexity 对数复杂度 
- O(2^n): Exponential Growth 指数
- O(n!): Factorial 阶乘

注意: 只看最高复杂度的运算

**如何看时间复杂度？**

根据 n 的不同情况，它会允许多少次。

例如：

**O(1)**

```java
int n  = 1000;
System.out.printInt("Hey, your input is:" + n);
```

```java
int n = 1000;
System.out.println("Hey - your input is: " + n); 
System.out.println("Hmm.. I'm doing more stuff with: " + n); 
System.out.println("And more: " + n);
```

不管 n 等于多少，它的程序只执行一次，所以它的时间复杂度为 O(1)。

**O(n)**

```java
for (int i = 1; i <= n; i++) {
  System.out.println("Hey - I'm busy looking at: " + i); 
}
```

程序会根据 n 的不同执行 n 的次数，和 n 是线性关系，所以它的时间复杂度为 O(n)。

**O(n^2)**

```java
for (int i = 1; i <= n; i++) { 
  for (int j = 1; j <=n; j++) {
    System.out.println("Hey - I'm busy looking at: " + i + " and " + j);
  } 
}
```

**O(log n)**

```java
for (int i = 1; i < n; i = i * 2) {
  System.out.println("Hey - I'm busy looking at: " + i);
}
```

如果 n 等于 4 ，那么函数体会执行 2 次，它的执行次数为 log2(n)，所以时间复杂度为 O(log n)。


## 算法的运用

不同的程序在写法不一样的话，它可能会导致时间复杂度不一样，例如从 1 加到 2 一只加到 n 的求和。

计算:1 + 2 + 3 + ... + n

主要有以下两种解法

**暴力求解**

```java
int y = 0;
for (int i = 1; i < n; i ++) {
  y += i;
}
```

直接从 1 循环累加到 n ，n 是多少就循环多少次，时间复杂度为 O(n)。

**求和公式**

```java
int y = n * (n + 1) / 2
```

无论 n 等于多少，程序只执行一次，时间复杂度为 O(1)。

## 递归的复杂度分析
把递归的执行顺序画出一个树结构，称之为递归状态的递归树。可以看一下例子：求 Fibonacci 数列的第 n 项目。

Fib: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

F(n) = F(n - 1) + F(n - 2)

Fibonacci 时间复杂度为 O(k^n)  k 是一个常数 k 的 n 次方，是一个指数级的，简单的递归求 Fibonacci 的话是非常慢的，时间复杂度为 O(2^n) 。


```java
int fib(int n) {
  if (n < 2) return n;
  return fib(n - 1) + fib(n - 2);
}
```


假设这时候的 n 是 6 ，要计算 F(6) , 判断 n(6) < 2 , 不满足，接着 return F(5) + F(4) ，所以要计算 F(6) 就要引出两个分支分别是 F(5) 和 F(4)。如果要计算 F(5) 就要计算 F(4) + F(3) ,同时 F(4) 这边需要 F(3) + F(2) 。

这里我们可以看到两个现象：

- 每多展开一层，运行的节点数就是上面一层的两倍。第一层 1 个节点，第二层 2 个节点，第三层 2^2 为 4 个节点，第四层 2^3 为 8 个节点，最后一层为 2^n 节点。
- 有重复的节点出现在执行的状态树。例如 F(6) =  F(5) + F(4) 和 F(5) = F(3) + F(4) 中的 F(4) 重复。

因此我们可以加一个缓存，或者用一个循环来写。

**递归复杂度分析主定理**

1. 二分查找法，一般发生在一个数列本身有序的时候，你要在有序的数列里面找到你要的目标数。如果一分为 2 它只查 1 边那么它的时间复杂度为 O(log n) 
2. 二叉树遍历，每次一分为二，每一边它是相等的时间复杂度下去，每个节点都会访问一次，且仅访问一次，根据公式法可以推断出它的运行时间为 O(n)。
3. 二维矩阵，是排序好的二维矩阵中进行的的二分查找。一维度数组二分查找时间复杂度为 O(log n)，二维数组二分查找时间复杂度为 O(n)。
4. 归并排序，所有排序最优的办法都是 O(nlog n) 。

## 空间复杂度
TBD

## 思考题

**1. 二叉树遍历 - 前序、中序、后序:时间复杂度是多少?**

通过主定理可以得到时间复杂度都是 O(n) , 这里的 n 代表二叉树的节点总数。不管前序、中序、后序，它遍历二叉树的时候每个节点访问且仅访问一次，所以总数限定于节点总数。

**2. 图的遍历:时间复杂度是多少?**

通过主定理可以得到时间复杂度都是 O(n) , 每个节点访问且仅访问一次，所以总数限定于节点总数。

**3. 搜索算法:DFS、BFS 时间复杂度是多少?**

不管深度优先、广度优先，时间复杂度因为访问的节点只访问一次，所以它的时间复杂度为 O(n)，n 是搜索空间的节点总数。

**4. 二分查找:时间复杂度是多少**

一分为 2 它只查 1 边那么它的时间复杂度为 O(log n) 。


## 参考

- [如何理解算法时间复杂度的表示法](https://www.zhihu.com/question/21387264)
- [主定理](https://zh.wikipedia.org/wiki/%E4%B8%BB%E5%AE%9A%E7%90%86)
- [Master theorem](https://en.wikipedia.org/wiki/Master_theorem_(analysis_of_algorithms))



