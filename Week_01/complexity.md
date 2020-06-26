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

**O(k^n)**

```java
int fib(int n) {
  if (n < 2) return n;
  return fib(n - 1) + fib(n - 2);
}
```

这里的 k 是一个常数 k 的 n 次方，是一个指数级的，简单的递归求 Fibonacci 的话是非常慢的。

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



