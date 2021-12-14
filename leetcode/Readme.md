[TOC]



# 算法思想

## 双指针

## 排序

### 快速排序

### 堆排序

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

   **medium**

  - [lc 129. Sum Root to Leaf Numbers](./lc_129.md)
  - [lc_131. Palindrome Partitioning](./lc_131.md)



### BFS

​	**medium**

- [lc 133. Clone Graph](./lc_133.md)

note: lc_126和lc_127，也太难了，需要再体会一下

### 二分查找

二分搜索题目有个很强烈的暗示，就是时间复杂度在O(log n)

- [lc_162. Find Peak Element](./lc_162.md)



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

  ​     **hard**

  - [lc 124. Binary Tree Maximum Path Sum](./lc_124.md)





## 贪心

## 数学

# 数据结构

## 位运算

## 二叉树

### 二叉树的遍历

二叉树的遍历包括了前序遍历、中序遍历、后序遍历以及层序遍历。

#### 前序、后序遍历

前序遍历和后序遍历，分别可以用recursive和iterative方法实现

- [lc_144. Binary Tree Preorder Traversal](./lc_144.md)]

- [lc_145. Binary Tree Postorder Traversal](./lc_145.md)

  

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



- [lc 104. Maximum Depth of Binary Tree [easy]](./lc_104.md)

- [lc 116. Populating Next Right Pointers in Each Node [medium]](./lc_116.md)

  note: 与lc_116类似的题目还有lc_117，lc_116可以通过递归和层序遍历完成，但是对于lc_117，由于给的输入只是普通的二叉树，所以只能通过层序遍历完成。

## 链表

链表中需要掌握的知识：

 - 链表的翻转

   ```python
   def reverseList(head):
     prev, cur = None, head
     while cur:
       tmp = cur.next
       cur.next = prev
       prev = cur
       cur = tmp
     return prev
   ```

   

 - 如何快速寻找单链表的中点（快慢指针）

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

   

对于奇数长度链表，返回的是最中间的节点；对于偶数长度链表，中间节点有两个，返回的是后面那个节点。

 - 如何判断链表是否存在环
 - 如果链表存在环，寻找环的入口
 - 寻找链表的倒数第k个元素





## 堆

## 哈希表

哈希表(hash table)就是一种以键-值（key-value）存储数据的结构，在python中dict和set都是一种hash table，使用哈希表，查找的时间复杂度为O(1)

- [lc 128. Longest Consecutive Sequence](./lc_128.md)

## 约瑟夫环

## [Level Order Traversal](#leetcode-87-scramble-string)

[test](./lc_87.md)



