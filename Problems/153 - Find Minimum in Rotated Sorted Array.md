---
tags:
  - array
  - binarySearch
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 153
First: March 27, 2025 5:16 PM
Watch Solution: false
---

# 153. Find Minimum in Rotated Sorted Array

[Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/?envType=problem-list-v2&envId=xoqag3yj)

**Topics**: Array, Binary Search

## Notes

快樂Binary Search 
但是有靈神的簡潔寫法：
[這](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array/solutions/1987499/by-endlesscheng-owgd/)

關鍵：和最後一個數比大小
兩邊都是開區間

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        minN = inf
        l, r = -1, len(nums)

        while l + 1 < r:
            mid = (l + r) // 2
            if nums[mid] <= nums[-1]:
                r = mid
            else:
                l = mid
        return nums[r]
```
