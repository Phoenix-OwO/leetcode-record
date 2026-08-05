---
tags:
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Weekly 513
First: 2026-08-02
Watch Solution: false
---
[link](https://leetcode.com/problems/count-subarrays-with-even-odd-ratio-i/description/)
這題也是暴力n 平方就會過，至於nlogn 的方法可以參考[[4013 - Count Subarrays With Even Odd Ratio II]]


```python
class Solution:
    def countRatioSubarrays(self, nums: list[int], a: int, b: int) -> int:
        ans = 0
        n = len(nums)
        for i in range(n):
            x = 0 # even
            y = 0 # odd
            for j in range(i, n):
                if nums[j] % 2 == 0:
                    x += 1
                else:
                    y += 1
                if y > 0 and x / y <= a / b:
                    ans += 1
        return ans
```

