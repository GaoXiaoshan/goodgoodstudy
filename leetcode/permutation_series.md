# 回文系列题目



## lc_31. Next Permutation()

这个题目，最开始看，真的没有看懂什么意思。

重新理解题目的意思：题目输入的是一组数，输出的是下一个回文组合，什么叫下一个回文组合呢，就是输出下一个比他更大的数字。

举个例子， 有数组 [1 2 7 4 3 1]，我们可以看到 7 4 3 1 已经是这个组合里最大的数组了，所以我们需要修改的是 2 7 4 3 1 这个组合，就是要把2这个数字换掉，再重排列。

第一步，怎么换？ 在 7 4 3 1 里面找个比2大的数字，也就是3，进行替换。 2 7 4 3 1 ---> 3 7 4 2 1；

​			     这个 3 7 4 2 1 并不是比  2 7 4 3 1 更大的数字里的第一个组合！比 2 7 4 3 1 更大的第一个组合

​				 是 3 1 2 4 7.

第二步是，替换后，对 3 后面的数字进行一个升序排列。



具体实现，还是上面这个example, 但是有个小trick，

step 1.  输入， [1 2 7 4 3 1]，从后往前，确定已经是最大数字的组合，也就是  [7 4 3 1] 。

step 2. 将这个最大数字的组合 [7 4 3 1]，逆序得到 [1 3 4 7]。

step2.  在已经逆序中的组合里寻找比该组合的前一位2大的数字，进行交换。 最终得到 [1 3 1 2 4 7]



```python
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        
        def reverse(l, r):
            while l < r:
                nums[l], nums[r] = nums[r], nums[l]
                l += 1
                r -= 1
        
        for i in range(len(nums)-1, 0, -1):
            if nums[i] > nums[i-1]:
                prev_i = i-1
                j = i
                reverse(i, len(nums)-1)
                for j in range(i, len(nums)):
                    if nums[j] > nums[prev_i]:
                        nums[prev_i], nums[j] = nums[j], nums[prev_i]
                        return
        
        reverse(0, len(nums)-1)
```

