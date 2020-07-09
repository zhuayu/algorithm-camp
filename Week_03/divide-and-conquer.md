# 分治、回溯的实现和特性

分治和回溯是递归的一个细分类，可以理解为是一个特殊一点的复杂一点的递归。

递归的重复性有最近的重复性和最优的重复性，最优的重复性就是动态规划，最近的重复性根据重复性的构造以及怎么分解就有了分治和回溯。


## 分治
分治是在递归状态树的时候，对于一个问题，可以分解成若干个子问题，最后对子问题进行组合。

**分治代码模板**分治模版主要有四个组成部分：


1. 递归终结条件 recursion terminator
1. 处理当前逻辑 process logic
1. 下探到下一层 drill down
1. 合并子结果 process and generate the final result
1. 清理当前层（ 可选：释放内存）reverse the current level status if needed
```python
def divide_conquer(problem, param1, param2, ...): 
  # recursion terminator 
  if problem is None: 
  print_result 
  return 
  # prepare data 
  data = prepare_data(problem) 
  subproblems = split_problem(problem, data) 
  # conquer subproblems 
  subresult1 = self.divide_conquer(subproblems[0], p1, ...) 
  subresult2 = self.divide_conquer(subproblems[1], p1, ...) 
  subresult3 = self.divide_conquer(subproblems[2], p1, ...) 
  …
  # process and generate the final result 
  result = process_result(subresult1, subresult2, subresult3, …)
  
  # revert the current level states
```


## 回溯
回溯法采用试错的思想，它尝试分布的去解决一个问题。在分步解决问题的过程中，当它通过尝试发现现有的分步答案不能得到有效的正确的解答的时候，它将取消上一步甚至是上几步的计算，再通过其他可能的分步解答再次尝试寻找问题的答案。

回溯法通常用最简单的递归方法来实现，在反复重复上述步骤后可能出现两种情况：


1. 找到一个可能存在的正确的答案；
1. 在尝试了所有可能的分步方法后宣告该问题没有答案；

在最坏的情况下，回溯法回导致一次复杂度为指数的时间计算。
