---
tags:
  - math
Difficulty Level: Medium
Rating: 17500
Need Review: false
Origin: Weekly 517
First: 2026-08-30
Watch Solution: false
---
[link](https://leetcode.com/problems/sum-of-decoded-numbers/)
就就是照做而已照做
那個pow 背後的概念是快速冪 就這樣


```python
class Solution:
    def sumDecoded(self, nums: list[int]) -> int:
        ans = 0
        MOD = (10 ** 9) + 7

        for num in nums:
            width = num % 10
            d = str(floor(num / 10))
            x = int(d[:width])
            y = int(d[width:])
            ans += pow(x, y, MOD)
            ans %= MOD
        return ans
```

