# Cheet Sheet 笔试

[TOC]

## 1.总

### 1.常见算法的时间复杂度：

二分查找、BST查找：logn

| 算法            | 时间                                   | 空间    | 描述                      |
| --------------- | -------------------------------------- | ------- | ------------------------- |
| 顺序表          |                                        |         |                           |
| 插入            | n                                      |         | 移动元素，平均n/2次       |
| 删除            | n                                      |         | 移动平均(n-1)/2次         |
| 按值查找        | n                                      |         |                           |
| 链表            |                                        |         |                           |
| 头尾插创建      | n                                      |         |                           |
| 按值/序查找     | n                                      |         |                           |
| 插入、删除      | 1                                      |         |                           |
| 二叉树          |                                        |         |                           |
| 创建二叉树      | n                                      | n       | 类似先序遍历              |
| 遍历            | n                                      | n       | 递归遍历node              |
| BST插入删除     | logn                                   |         |                           |
| 图              |                                        |         |                           |
| 邻接矩阵        |                                        | V2      |                           |
| 邻接表          |                                        | V+E(2E) |                           |
| 邻接矩阵BFS     | V2                                     |         |                           |
| 邻接表BFS       | V+E                                    |         |                           |
| 邻接矩阵DFS     | V2                                     |         |                           |
| 邻接表BFS       | V+E                                    |         |                           |
| prim            | V2，改进可达ElogV                      |         | 稠密图                    |
| kru             | ElogE                                  |         | 边稀疏，顶点多            |
| dijk            | V2                                     |         |                           |
| floyd           | V3                                     |         |                           |
| 拓扑排序        | V+E                                    |         |                           |
| 平均查找长度ASL |                                        |         |                           |
| 顺序查找        | $\sum_{i=1}^{n}P_i(n-i+1)=\frac{n+1}2$ |         | 不成功n+1，平均为二者平均 |
| 有序顺序查找    | $ASL_{false}=n/2+n/(n+1)$              |         |                           |
| 二分查找        | logn                                   |         |                           |

![image-20240617222126867](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617222126867.png)

### 2.数据结构：

#### ·逻辑结构：

​	线性表：数组、链表

​	非线性表：树、堆、图、哈希表

#### ·物理（存储）结构：数据在计算机内存中的存储方式

​	连续：数组适合访问，不适合增删

​	分散：链表适合增删，不适合访问

## 2.线性结构、哈希、栈和队列

### 1.处理散列表的冲突：

开放地址法：迭代哈希函数（新地址）；链地址法：同义词链表

### 2.栈

#### 中序转后序：调度场算法

```python
以下是 Shunting Yard 算法的基本步骤：
1. 初始化运算符栈和输出栈为空。
2. 从左到右遍历中缀表达式的每个符号。
   - 如果是操作数（数字），则将其添加到输出栈。
   - 如果是左括号，则将其推入运算符栈。
   - 如果是运算符：
     - 如果运算符的优先级大于运算符栈顶的运算符，或者运算符栈顶是左括号，则将当前运算符推入运算符栈。
     - 否则，将运算符栈顶的运算符弹出并添加到输出栈中，直到满足上述条件（或者运算符栈为空）。
     - 将当前运算符推入运算符栈。
   - 如果是右括号，则将运算符栈顶的运算符弹出并添加到输出栈中，直到遇到左括号。将左括号弹出但不添加到输出栈中。
3. 如果还有剩余的运算符在运算符栈中，将它们依次弹出并添加到输出栈中。
4. 输出栈中的元素就是转换后的后缀表达式。
```

#### 合法出栈序列：

```python
先判断是否在原栈里，如果在就出栈入栈直到该元素，如果不在就必须是新栈顶，否则不合理
```

## 3.树

### 1.二叉树

满二叉树：所有层的节点都被填满

完全二叉树：只有最底层的节点未被填满，且从左向右填充

完满二叉树：所有节点的度为0或2

#### 1.二叉树的遍历：

前中后序，按层次遍历

前中序转后序：

```python
前序定根，中序分左右子树，递归
```

#### 2.Huffman树：

Huffman树的带权路径长度：每个源码节点乘上到这个节点的路径长度求和

![image-20240617201016613](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617201016613.png)

#### 3.堆：

二叉堆的插入、删除：

```python
插入：插入一个元素到末位，从下往上递归判断是否交换
删除：去除顶端元素，将末位元素挪至顶端，从上向下递归判断是否交换
```

二叉堆的性质：画图判断，基本是二倍关系

#### 4.字符串的KMP算法：

计算前缀表-根据前缀表移动两个指针进行匹配

next的作用：找到相等的前缀和后缀位置

## 4.图：

### 1.表示方法：

邻接表：外层表示节点，内层表示每个节点相连的节点-稀疏

邻接矩阵：二维矩阵，格中位置表示边的权重

### 2.遍历方法，dfs、bfs：

#### 最大权值连通块：

![image-20240617213307459](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617213307459.png)

#### 有向图判环：

![image-20240617213349908](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617213349908.png)

### 3.图的算法：

#### 1.单源最短路径-Dijkstra：表记录最短距离，每次选择最近未处理节点进行更新

![image-20240617213557435](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617213557435.png)

#### 2.每对顶点之间最短路-Floyd算法：

![image-20240617213730067](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617213730067.png)

#### 3.最小生成树-Prim算法：贪心，对于每个节点在现有的树中找最短的路径

![image-20240617221025132](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617221025132.png)

#### 4.最小生成树-Kruskal算法：贪心，把边排序，逐一处理，不可成环

图的连通性：

1. **连通分量（Connected Component）：** 在无向图中，一个连通分量是指图中的一个极大连通子图，其中的任意两个节点都可以通过图中的边互相到达。连通分量可以理解为无向图的极大连通子图。

2. **强连通分量（Strongly Connected Component）：** 在有向图中，一个强连通分量是指图中的一个极大子图，其中的任意两个节点都可以通过有向路径互相到达。强连通分量可以理解为有向图的极大连通子图。

![image-20240617213951439](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617213951439.png)

#### 5.拓扑排序-Kahn算法：维护一个入度为零的表

![image-20240617214122340](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617214122340.png)

## 5.排序

![image-20240617214557063](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240617214557063.png)

### 1.冒泡排序：

逐个交换，每轮确定最后一个值O(n2)

### 2.选择排序：

每次遍历选择最大值放在最后，n-1轮O(n2)一般比冒泡快

### 3.插入排序：

维护有序子列表，逐个插入新元素O(n2)

### 4.希尔排序：递减增量排序

增量从n到1，最后插入排序O(n)~O(n2)之间

### 5.归并排序：

拆分成1或2个元素，排序，两个列表合并的时候通过比较左边第一个数字大小进行合并O(nlogn)

### 6.快速排序：

找到一个基准值，例如第一个，对其余列表移动左右指标，左指标找到第一个大于ptvot的，右指标找到第一个小于pivot的，两个互换位置，继续行进，直到只剩一个元素，前一个即为pivot的位置，交换pivot和该位置，此时左右分别快排

快排不需要归并排序的额外空间，一般是O(nlogn)但是最坏情况O(n2)

