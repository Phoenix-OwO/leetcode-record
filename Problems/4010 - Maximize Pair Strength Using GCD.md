---
tags:
Difficulty Level: Easy
Rating: 1250
Need Review: false
Origin: Weekly 513
First: 2026-08-02
Watch Solution: false
---
[link](https://leetcode.com/problems/maximize-pair-strength-using-gcd/description/)
暴力即可過！

```python
class Solution:
    def maxPairStrength(self, nums: list[int]) -> int:
        n = len(nums)
        ans = 0
        
        for i in range(n):
            for j in range(i + 1, n):
                ans = max(nums[i] * nums[j] // (gcd(nums[i], nums[j]) ** 2), ans)
        return ans
```

