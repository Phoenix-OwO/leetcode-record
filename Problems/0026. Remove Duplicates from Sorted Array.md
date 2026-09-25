---
tags:
  - twoPointers
  - array
Difficulty Level: Easy
Rating:
Need Review: false
Origin:
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)
一樣是left pointer 跟right pointer，left pointer 用來記錄目前有幾個不一樣的元素（也就是說等等的新元素要放在哪一個位置）
right pointer 可以用for 圈解決


```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i, k = 0, 1
        n = len(nums)

        for i in range(1, n):
            if nums[i] != nums[i-1]:
                nums[k] = nums[i]
                k += 1
        return k
        
```

同樣是換來換去的two pointer 
[[27 - Remove Element]]

類似的題目，但是今天每個元素最多可以有k 個
[[80 - Remove Duplicates from Sorted Array II]]