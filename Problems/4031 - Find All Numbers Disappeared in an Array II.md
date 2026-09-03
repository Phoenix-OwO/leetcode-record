---
tags:
  - sorting
Difficulty Level: Medium
Rating: 1416
Need Review: false
Origin: Weekly 516
First: 2026-08-23
Watch Solution: false
---
[link](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array-ii/description/)
就是interval 題，但是要注意一些特殊狀況，比如整個nums 裡面都小於lower 或大於upper 
還有就是剛好upper 有在數列裡面 
大概是這幾種
要看到第一眼就想到 加油

```python
class Solution:
    def findDisappearedNumbers(self, nums: list[int], lower: int, upper: int) -> list[list[int]]:
        nums = sorted(list(set(nums)))
        if lower > nums[-1] or upper < nums[0]:
            return [[lower, upper]]
        
        ans = []
        l = lower
        for num in nums:
            if num < lower:
                continue
            elif num <= upper:
                r = num - 1
                if num == l:
                    l += 1
                if r >= l:
                    ans.append([l, r])
                    l = num + 1
            else:
                r = min(upper, num - 1)
                if r >= l:
                    ans.append([l, r])
                l = num + 1
                break
        if upper >= l:
            ans.append([l, upper])
        return ans
```

