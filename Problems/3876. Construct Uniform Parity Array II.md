---
tags:
  - array
  - math
Difficulty Level: Medium
Rating: 1443
Need Review: false
Origin: 09/03 Daily
First: 2026-09-03
Watch Solution: false
---
[link](https://leetcode.com/problems/construct-uniform-parity-array-ii/description/?envType=daily-question&envId=2026-09-03)

```python
class Solution:
    def uniformArray(self, nums1: list[int]) -> bool:
        nums1.sort(reverse = True)
        cnt0, cnt1 = 0, 0
        for num in nums1:
            if num % 2 == 0:
                cnt0 += 1
            else:
                cnt1 += 1
        checkOdd, checkEven = True, True
        for num in nums1:
            if num % 2 == 0:
                cnt0 -= 1
            else:
                cnt1 -= 1
            if num % 2 == 0 and cnt1 == 0:
                checkOdd = False
            if num % 2 == 1 and cnt1 == 0:
                checkEven = False
        return checkOdd or checkEven
```

