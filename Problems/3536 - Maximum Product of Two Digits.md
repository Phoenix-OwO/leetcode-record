---
tags:
  - sorting
  - math
Difficulty Level: Easy
Rating: 1199
Need Review: false
Origin: 07/25 Daily
First: 2026-07-25
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-product-of-two-digits/?envType=daily-question&envId=2026-07-27)
懶得想，隨便sort 一下

```python
class Solution:
    def maxProduct(self, n: int) -> int:
        digits = []
        for c in str(n):
            digits.append(int(c))

        digits.sort(reverse = True)
        return digits[0]*digits[1]
        
```

