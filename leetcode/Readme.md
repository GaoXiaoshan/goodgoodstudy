[TOC]



# 算法思想

## 双指针

## 排序

### 快速排序

### 堆排序

### 归并排序

## 搜索

### DFS

### BFS

### 二分查找

### 回溯

## 动态规划

动态规划解决的问题一般都是求最值，中心思想就是把这个问题通过分解成子问题，找最优子结构。可以考虑**自下而上**和**自上而下**两种求解方式。考虑到很多子问题会被重复求解，在动态规划中常常使用自下而上对问题进行求解，每个子问题会结果会被储存下来。



**hard**

- [lc 124. Binary Tree Maximum Path Sum](./lc_124.md)

## 贪心

## 数学

# 数据结构

## 位运算

## 二叉树

### 二叉树的遍历

二叉树的遍历包括了前序遍历、中序遍历、后序遍历以及层序遍历。

#### 层序遍历

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

## 堆

## 约瑟夫环

## [Level Order Traversal](#leetcode-87-scramble-string)

[test](./lc_87.md)



