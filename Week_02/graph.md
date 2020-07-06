# 2. 图的实现和特性

![image.png](https://cdn.nlark.com/yuque/0/2020/png/166094/1593739481079-901a4b33-fd9b-4a61-9b2c-0d71735edcec.png#align=left&display=inline&height=308&margin=%5Bobject%20Object%5D&name=image.png&originHeight=308&originWidth=952&size=120208&status=done&style=none&width=952)

## 图的属性

图的简单定义，有点有边。在数学上用 Graph(V, E) 来表示。

V - verter：点

1. 度（ 表示一个点有多少个边） - 入度，出度 （ 如果边是无向的，那么入度等于出度）
2. 点与点之间是否联通（ 直接有边相联，还是要绕很远 ）

E - edge：边

1. 有向和无向（ 单行、双行）
2. 权重（ 边长 ）

## 图的表示和分类
![image.png](./images/graph-1.md)

图的表示有两种，邻接矩阵和邻接表。都是二维的数据结构。纵向是它们点的下标，区别在于横向：

- 邻接矩阵的横向点也是点的下标，矩阵中的内容是他们点与点直接的边长。（ 如果有权重就是权重，无权重就 0/1 ）
- 邻接表的横向值的是当前点直接对应能连接到的另一个点。（ 例如：0->1-> 3 代表 0 和 1/3 向连接 ）

以上没有方向没有权重的称为无向无权图。

当一个边有了方向，这时候矩阵就不再是对称的矩阵，称之为有向无权图。

![image.png](./images/graph-2.md)

如果边的长度不再是 0 和  1 ，而是有相应边长这样的属性，但是没有方向，这时候就变成了无向有权图。

![image.png](./images/graph-2.md)

## 图的算法

DFS 代码 - 递归写法
>  visited = set() # 和树中的DFS最大区别

```python
    
def dfs(node, visited):
  if node in visited: # terminator
    # already visited
    return
  visited.add(node)
  # process current node here.
  ...
  for next_node in node.children(): 
        if not next_node in visited:
      dfs(next_node, visited)
```

BFS 

```python
def BFS(graph, start, end): queue = []
  queue.append([start])
  visited = set() # 和数中的BFS的最大区别
  while queue:
    node = queue.pop() visited.add(node)
    process(node)
    nodes = generate_related_nodes(node) queue.push(nodes)
```

## 思考题

- 自己画一下有向有权图

## 参考链接

- 连通图个数：[ https://leetcode-cn.com/problems/number-of-islands/](https://leetcode-cn.com/problems/number-of-islands/)
- 拓扑排序（Topological Sorting）：[ https://zhuanlan.zhihu.com/p/34871092](https://zhuanlan.zhihu.com/p/34871092)
- 最短路径（Shortest Path）：Dijkstra [https://www.bilibili.com/video/av25829980?from=search&seid=13391343514095937158](https://www.bilibili.com/video/av25829980?from=search&seid=13391343514095937158)
- 最小生成树（Minimum Spanning Tree）：[ https://www.bilibili.com/video/av84820276?from=search&seid=17476598104352152051](https://www.bilibili.com/video/av84820276?from=search&seid=17476598104352152051)
