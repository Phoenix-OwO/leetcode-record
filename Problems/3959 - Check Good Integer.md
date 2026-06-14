---
tags:
  - enumeration
Difficulty Level: Easy
Rating:
Need Review: false
Origin:
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/check-good-integer/)
照做即可

```python
class Solution:
    def checkGoodInteger(self, n: int) -> bool:
        sS, dS = 0, 0
        while n > 0:
            d = n % 10 
            n //= 10
            sS += d ** 2
            dS += d
        return sS - dS >= 50
```

