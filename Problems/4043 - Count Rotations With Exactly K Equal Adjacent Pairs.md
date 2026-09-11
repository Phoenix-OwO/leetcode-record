---
tags:
Difficulty Level: Easy
Rating:
Need Review: false
Origin: Weekly 518
First: 2026-09-09
Watch Solution: false
---
[link](https://leetcode.com/problems/count-rotations-with-exactly-k-equal-adjacent-pairs/)

```python
class Solution:
    def countRotations(self, s: str, k: int) -> int:
        n = len(s)
        ans = 0

        def countAdj(int: i):
            s1 = s[i:] + s[:i]
            cnt = 0
            for j in range(1, n):
                if s1[j] == s1[j - 1]:
                    cnt += 1
            return cnt
        
        for i in range(n):
            curr = countAdj(i)
            if curr == k:
                ans += 1
        
        return ans
```

