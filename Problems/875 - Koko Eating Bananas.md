---
tags:
  - array
  - binarySearch
Difficulty Level: Medium
Rating: 1765
Need Review: false
Origin: LC 875
First: March 26, 2025 7:05 PM
Watch Solution: false
---

# 875. Koko Eating Bananas

[Link](https://leetcode.com/problems/koko-eating-bananas/description/)

**Topics**: Array, Binary Search

binary search on ans 的經典題，要小心一開始left bound 要取在1 ，不是min 或是 0
## Notes

```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        l = 1
        r = max(piles)
        
        while l <= r:
            mid = (l + r) // 2
            cnt = sum(ceil(p/mid) for p in piles)
            if cnt <= h:
                r = mid - 1
            else:
                l = mid + 1
        return l

```

