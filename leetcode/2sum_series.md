[toc]



## lc_1. Two Sum

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

 

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```



```python
# 知识点：hash table
def twoSum(nums, target):
  num_dict = {}
  for index,val in enumerate(nums):
    tmp = target-val
    if tmp in num_dict:
      return [index, num_dict[tmp]]
    num_dict[val] = index
```



## lc_167. Two Sum II - Input Array Is Sorted

Given a **1-indexed** array of integers `numbers` that is already **sorted in non-decreasing order**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return *the indices of the two numbers,* `index1` *and* `index2`*, **added by one** as an integer array* `[index1, index2]` *of length 2.*

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

 

**Example 1:**

```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```

```python
# 知识点：双指针，hash tabel
# Solution 1. 双指针 numbers that is already sorted in non-decreasing order 是个非常明显的提示
def twoSum(numbers, target):
  l, r = 0, len(numbers)-1
  while l < r:
    if (numbers[l]+numbers[r]) == target:
      return [l+1, r+1]
    elif (numbers[l]+numbers[r]) < target:
      l += 1
    else:
      r -= 1
```



## lc_15. 3 Sum

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.



**Example 1:**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```



**思路**：2sum题相似，使用双指针。区别在于，题目要求写出所有满足target的组合，这个暗示了solution不是唯一的，所以当tmp == target后，l, r 还要继续移动。并且nums中，存在重复的数字，所以为了避免出现重复的组合，当l, r遇见相同的数字时，需要跳过。

```python
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        res = []
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                tmp = nums[i] + nums[l] + nums[r]
                if tmp == 0:
                    res.append([nums[i], nums[l], nums[r]])
                    while l < r and nums[l] == nums[l+1]: l += 1
                    while l < r and nums[r-1] == nums[r]: r-= 1
                    l += 1
                    r -= 1
                elif tmp < 0:
                    l += 1
                else:
                    r -= 1
        return res
```



## lc_16. 3Sum Closest

Given an integer array `nums` of length `n` and an integer `target`, find three integers in `nums` such that the sum is closest to `target`.

Return *the sum of the three integers*.

You may assume that each input would have exactly one solution.

 

**Example 1:**

```
Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```



```python
# 知识点，双指针，思路和 twoSum II 是一样的，只不过多了一层循环
def threeSumClosest(self, nums: List[int], target: int) -> int:
  nums.sort()
  res = nums[0] + nums[1] + nums[2]
  leng = len(nums)
  for i in range(leng):
    l, r = i+1, leng-1
    while l<r:
      tmp = nums[i] + nums[l] + nums[r]
      if tmp == target:
        return tmp
      elif tmp < target:
        l += 1
      else:
        r -= 1
      if abs(target-res) > abs(target-tmp):
        res = tmp
  return res
```



## lc_18. 4Sum (K-Sum)

Given an array `nums` of `n` integers, return *an array of all the **unique** quadruplets* `[nums[a], nums[b], nums[c], nums[d]]` such that:

- `0 <= a, b, c, d < n`
- `a`, `b`, `c`, and `d` are **distinct**.
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in **any order**.

 

**Example 1:**

```
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```



**思路：** 2sum + 递归， 这个题目需要好好体会！ 并且能扩展到 k-sum。

```python
def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        
        def nSum(nums, target, n, path, res):
            if nums[0]*n > target or nums[-1]*n < target or n < 2 or len(nums)<n:
                return 
            if n == 2:
                # 2sum
                l, r = 0, len(nums)-1
                while l < r:
                    tmp = nums[l] + nums[r]
                    if tmp == target:
                        res.append(path+[nums[l], nums[r]])
                        while l < r and nums[l+1] == nums[l]: l+= 1
                        while l < r and nums[r-1] == nums[r]: r-= 1
                        l += 1
                        r -= 1
                    elif tmp < target:
                        l += 1
                    else:
                        r -= 1
            else:
                for i in range(len(nums)-n+1):
                    if i == 0 or (i>0 and nums[i] != nums[i-1]):
                        nSum(nums[i+1:], target-nums[i], n-1, path+[nums[i]], res)
            return 
            

        nums.sort()
        res = []
        nSum(nums, target, 4, [], res)
        return res
```

