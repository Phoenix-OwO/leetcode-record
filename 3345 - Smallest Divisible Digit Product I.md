---
tags:
  - math
  - enumeration
Difficulty Level: Easy
Rating: 1235
Need Review: false
Origin: 08/06 Daily
First: 2026-08-06
Watch Solution: false
---
[link](https://leetcode.com/problems/smallest-divisible-digit-product-i/description/?envType=daily-question&envId=2026-08-06)
暴力照做就好，甚至因為t 很小，所以不用管有沒有可能組不出t。

```python
class Solution:
    def smallestNumber(self, n: int, t: int) -> int:
        def prod(i):
            x = 1
            while i > 0:
                x *= i % 10
                i //= 10
            return x
        while n:
            if prod(n) % t == 0:
                return n
            n += 1
            
```

