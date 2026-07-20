---
tags:
  - numberTheory
Difficulty Level: Easy
Rating: 1184
Need Review: false
Origin: 07/18 Daily
First: 2026-07-12
Watch Solution: false
---
[link](https://leetcode.com/problems/find-greatest-common-divisor-of-array/description/?envType=daily-question&envId=2026-07-18)
照做就好

```python
class Solution:
    def findGCD(self, nums: List[int]) -> int:
        return gcd(min(nums), max(nums))
```

