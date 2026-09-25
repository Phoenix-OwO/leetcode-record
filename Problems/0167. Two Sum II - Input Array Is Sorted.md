---
tags:
  - array
  - binarySearch
  - twoPointers
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 167
First: March 26, 2025 6:58 PM
Watch Solution: false
---

# 167. Two Sum II - Input Array Is Sorted

[Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/submissions/1572362864/)

**Topics**: Array, Binary Search, Two Pointers

## Notes

binary search 基本簡單題 記得 關鍵字: sorted !

```python 
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l, r = 0, len(numbers) - 1

        while l <= r:
            if numbers[l] + numbers[r] == target:
                return [l + 1, r + 1]
            elif numbers[l] + numbers[r] < target:
                l += 1
            else:
                r -= 1
```

