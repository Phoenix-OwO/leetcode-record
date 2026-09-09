---
tags:
  - slidingWindow
  - enumeration
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Weekly 518
First: 2026-09-09
Watch Solution: false
---
[link](https://leetcode.com/problems/count-good-cyclic-rotations/description/)

```python
class Solution:
    def countGoodRotations(self, nums: list[int]) -> int:
        total = sum(nums)
        n = len(nums)
        curr = sum(nums[:n//2])
        ans = 0
        nums += nums

        for i in range(n//2, n + n//2):
            curr += nums[i] - nums[i - n//2]
            if curr > total - curr:
                ans += 1
        return ans
        
```

