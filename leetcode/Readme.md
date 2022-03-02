[TOC]

# 技巧总结

- 输入是有序，时间复杂度O(logn)，二分法
- 



# 算法思想

## 双指针

双指针明显的提示

1. non-decreasing order array， 比如remove duplicates系列的题目
2. one pass with constant memory

### 左右指针



- [lc_11. Container With Most Water](./lc_11.md)
- [2sum系列](./2sum_series.md)
- [lc_42. Trapping Rain Water](./lc_42.md)

### 快慢指针



### 双指针plus

除了需要双指针进行记录外，还需要一个额外的cur指针进行数组的遍历，那么一共是三个指针

- [lc_75. Sort  Colors](./lc_75.md)



## 滑动窗口

- [lc_567. Permutation in String](lc_567.md)

## 

## 排序

### 快速排序

### 堆排序

- [lc_149. Max Points on a Line](./lc_149.md)

### 归并排序

## 搜索

### DFS

- DFS 和 回溯 之间的联系

DFS在进行一个树的深度搜索时，当搜索完当前路径，必然会后退一步，进行该节点另一部分的搜索，所以这个过程就自然的产生了回溯这个步骤。

- DFS的三要素

DFS本质上就是一种暴力穷举法，穷举的对象是一个决策树。在这个问题里面有三个要素：路径，搜索空间，结束条件。

- DFS模版

```python
results = []
def dfs(path, space):
  if 满足结束条件:
    results.add(path)
    return
  for 选择 in 选择列表:
    #做选择
    dfs(path_new, space_new)
    # 撤销选择, 有时候并不是必须的
```

- 题

   - [lc 129. Sum Root to Leaf Numbers](./lc_129.md)
  - [lc_130. Surrounded Regions](lc_130.md)
  - [lc_131. Palindrome Partitioning](./lc_131.md)
  
  这里dfs和前面的有一点不一样，需要使用一个visited数组，或者其他trick标记已经见过的元素
  
  - [lc_200. Number of Islands](./lc200.md)
  
  涉及回溯，但是与模版有一点区别，有点trick
  
  - [lc_22. Generate Parentheses](./lc_22.md)

### BFS

- [lc 133. Clone Graph](./lc_133.md)

- [lc_207_210. Course Schedule Series ](lc_207_210.md) 

  note: 山景城一姐讲解的非常详细了 https://www.youtube.com/watch?v=fskPWs3Nuhc 



note: lc_126和lc_127，也太难了，需要再体会一下



### 二分查找

二分搜索题目有个很强烈的暗示，就是输入的数组已经是有序的，且时间复杂度在O(log n)

- [lc_162. Find Peak Element](./lc_162.md)
- [lc_275. H-Index II](lc_275.md)



## 动态规划

- 动态规划的思想：

  动态规划解决的问题一般都是**求最值**，中心思想就是**把这个问题分解成子问题求解，通过求解子问题的最优来得到问题最终的最优解。**

  在这个子问题求解的过程中，会产生很多重复的子问题，所以这时就需要一个**dp table**来对这些子问题的解进行一个存储，避免进行不必要的计算。

  动态规划有两种求解思路：**自下而上**和**自上而下**。

- 动态规划的三要素：base case， 状态转移方程，dp table

- 入门例子：斐波那契数列 

  - 斐波那契数列，求第n个数字

     1， 1， 2， 3， 5， ...，n

    斐波那契数列f(n)的规律：当 n = 1, 2 时 f(n) = 1; 当 n > 2时， f(n) = f(n-1) + f(n-2)





- 题

  - [lc 124. Binary Tree Maximum Path Sum](./lc_124.md)





## 贪心

## 数学

[lc_189. Rotate Array](./lc_189.md)



## 回文系列

[permutation_series](./permutation_series.md)

### 数的乘法

- [lc_43. Multiply Strings](./lc_43.md)

- [lc_172. Factorial Trailing Zeroes](./lc_172.md) 这个题很tricky，和算法有关不大。。更像脑筋急转弯



### 数的除法

- [lc_166. Fraction to Recurring Decimal](./lc_166.md)

# 数据结构

## 位逻辑运算

### 左移右移运算符

- 左移运算符 << 与右移运算符 >> 的优先级高于与&

- 1 << n，就是2^n

```shell
>>> 1 << 8
256
>>> 1 << 4
16
>>>
```

### 异或 ^

“^” 为按位异或 XOR 运算符

- [lc_389. Find the Difference](lc_389.md)

### 与运算 &

- 涉及到排列组合的题目，可以通过左移与与操作进行
  - [lc_78_90. Subsets](lc_78.md)

### 求一个数二进制中1的个数

```python
# solution 1. 位操作
def countBits(num):
  cnt = 0
  while num:
    cnt += num & 1
    num = num >> 1
  return cnt

# solution 2. 数学
def countBits(num):
  if num == 0:
    return 0 
  # num = 2*n or 2*n + 1
  res = countBits(num//2) + num%2
  return res
```



## 二叉树

### 二叉树深度

给定一个完全二叉树，求取深度

```python
def getDepth(root):
  if not root:
    return 0
  return 1 + getDepth(root.left)
```



给定一任意二叉树，求取其最大深度

```python
def maxDepth(root):
  if not root:
    return 0
  return 1 + max(maxDepth(root.left), maxDepth(root.right))
```



- [lc_110. Balanced Binary Tree](./lc_110.md)



### 二叉树的遍历

二叉树的遍历包括了前序遍历、中序遍历、后序遍历以及层序遍历。

#### 前序、中序、后序遍历

前序遍历、中序遍历和后序遍历，分别可以用recursive和iterative方法实现。注意，处理输入的root节点是空节点的情况。



- [lc_144. Binary Tree Preorder Traversal](./lc_144.md)

- [lc_145. Binary Tree Postorder Traversal](./lc_145.md)

  

  中序

- [lc_94. Binary Tree Inorder Traversal](./lc_94.md)

- [lc_173. Binary Search Tree Iterator](./lc_173.md)

- [lc_98. Validate Binary Search Tree](./lc_98_99.md)

- [lc_99. Recover Binary Search Tree](./lc_98_99.md)

   

####          层序遍历               

```python
def levelOrderTraversal(root:'Node'):
  if not root:
    return 0
  tree = [root]
  while tree:
    # 利用for循环和队列来控制同一层节点
    for _ in range(len(tree)):
      tmp = tree.pop(0)
      if tmp.left:
        tree.append(tmp.left)
      if tmp.right:
        tree.append(tmp.right)
```



- [lc 104. Maximum Depth of Binary Tree](./lc_104.md)

- [lc_101.Symmetric Tree](./lc_101.md)

- [lc 116. Populating Next Right Pointers in Each Node](./lc_116_117.md)

- [lc 117. Populating Next Right Pointers in Each Node II](./lc_116_117.md)

- [lc_199. Binary Tree Right Side View](./lc_199.md)

  note: 与lc_116类似的题目还有lc_117，lc_116可以通过递归和层序遍历完成，但是对于lc_117，由于给的输入只是普通的二叉树，所以只能通过层序遍历完成。



#### 基于树的结构，可以通过bfs, dfs方法完成的

- [lc_100. Same Tree](lc_100.md)

- [lc 116. Populating Next Right Pointers in Each Node](./lc_116_117.md)



### 二叉搜索树

## 链表

链表中需要掌握的操作：

### 链表的合并

- [lc_02. Add Two Numbers](lc_02.md)
- [lc_21. Merge Two Sorted Lists](lc_21.md)  --->  [lc 148. Sort List](./lc_148.md)



### 链表的元素删除

- [lc_19. Remove Nth Node From End of List](lc_19.md)



### 链表的翻转 

```python
# Solution 1. iteration
def reverseList(head):
  prev = None
  while head:
    tmp = head.next
    head.next = prev
    prev = head
    head = tmp
  return prev

# Solution 2. recursion

def reverseList(head):
  
  def _reverse(node, prev):
    if not node:
      return prev
    n = node.next
    node.next = prev
    return _reverse(n, node)
  
  return _reverse(head, None)

# Solution3. revursion ++
def reverseList(self, head):
  if not head or not head.next:
    return head

  new_head = self.reverseList(head.next)
  head.next.next = head
  head.next = None
  return new_head
```

- [lc_206. Reverse Linked List](./lc_206.md)

- [lc_92. Reverse Linked List II](./lc_92.md)

- [lc_143. Reorder List](./lc_143.md)

  

链表的反转一系列问题（递归的思路）,相关知识点请看 [递归反转链表的一部分](https://github.com/labuladong/fucking-algorithm/blob/master/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E7%B3%BB%E5%88%97/%E9%80%92%E5%BD%92%E5%8F%8D%E8%BD%AC%E9%93%BE%E8%A1%A8%E7%9A%84%E4%B8%80%E9%83%A8%E5%88%86.md)

- 反转整个链表 [lc_206. Reverse Linked List](./lc_206.md)

- 反转链表前N个节点 

- 反转指定区间的链表 [lc_92. Reverse Linked List II](./lc_92.md)

- 按照k个一组反转链表 [lc_25. Reverse Nodes in k-Group](./lc_25.md)

  

### 寻找链表的某个点

- 寻找链表的倒数第k个元素
- 如何快速寻找单链表的中点（快慢指针）
  - [lc_143. Reorder List](./lc_143.md)
  - [lc_109. Convert Sorted List to Binary Search Tree](./lc_109.md)
  - [lc_876. Middle of the Linked List](./lc_876.md) 	
  - [lc_143. Reorder List](./lc_143.md)


   ```python
   # 奇数长度链表，返回最中间节点；偶数长度链表，返回中间两个节点中后面的那一个
   def middleNode(head):
     slow, fast = head, head
     while fast and fast.next:
       slow = slow.next
       fast = fast.next.next
     return slow
   ```

   ​     对于奇数长度链表，返回的是最中间的节点；对于偶数长度链表，中间节点有两个，返回的是后面那个节 点。

 

### 如何判断链表是否存在环 && 如果链表存在环，寻找环的入口

- [lc_141. Linked List Cycle](./lc_141.md)

- [lc_142. Linked List Cycle II](./lc_142.md)

- [lc 160. Intersection of Two Linked Lists](./lc_160.md)

  

### 链表与排序结合

- [lc_147. Insertion Sort List](./lc_147.md)
- [lc 148. Sort List](./lc_148)

​        

## 堆

## 哈希表

哈希表(hash table)就是一种以键-值（key-value）存储数据的结构，在python中dict和set都是一种hash table，使用哈希表，查找的时间复杂度为O(1)

- [lc 128. Longest Consecutive Sequence](./lc_128.md)

## 约瑟夫环

[test](./lc_87.md)



# 一些需要掌握的tricks

## prefix sum

 
