# leetcode 84. Largest Rectangle in Histogram (hard)

Given an array of integers `heights` representing the histogram's bar height where the width of each bar is `1`, return *the area of the largest rectangle in the histogram*.

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg)

```
Input: heights = [2,1,5,6,2,3]
Output: 10
Explanation: The above is a histogram where width of each bar is 1. The largest rectangle is shown in the red area, 
which has an area = 10 units.
```

**Example 2:**

![img](https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg)

```
Input: heights = [2,4]
Output: 4
```

 

**Constraints:**

- `1 <= heights.length <= 105`
- `0 <= heights[i] <= 104`



**解题思路**

1. 遍历*heights*数组，对于当前的*bar*与前面的*bar*组成的长方形面积取决于整个长方形里高度最低的bar。
2. 使用单调递增栈去维持遍历过的*bar*，当当前的*bar*高度比栈顶元素低，那么说明此*bar*不能与前面的元素形成*rectangle*
3. 此时需要对栈内的元素进行处理，计算面积。



```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
      # 为了处理heights中的第一个元素
      heights.append(0)
      stack = [-1]
      ans = 0
      for i in range(len(heights)):
        while heights[i] < heights[stack[-1]]:
          h = heights[stack.pop()]
          w = i - stack[-1]-1
          ans = max(ans, h*w)
         stack.append(i)
       
```

