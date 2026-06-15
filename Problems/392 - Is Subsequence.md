---
tags:
  - twoPointers
  - string
  - dp
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/is-subsequence/?envType=study-plan-v2&envId=top-interview-150)
一開始以為要for 迴圈去看t 的起始點，但仔細想想如果從 i + 1 開始可以走到，代表從i 開始也一定可以走到，所以沒有必要這麼做，直接從頭開始就好
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        l1, l2 = len(s), len(t)
        p1, p2 = 0, 0

        while p1 < l1 and p2 < l2:
            if s[p1] == t[p2]:
                p1 += 1
                p2 += 1
            else:
                p2 += 1
        if p1 == l1:
            return True
        
        return False 
```

