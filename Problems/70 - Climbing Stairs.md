---
tags:
  - dp
  - math
  - memorization
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-22
Watch Solution: false
---
[link]()

```python
class Solution(object):
    def climbStairs(self, n):
        f0, f1 = 1, 1
        
        for i in range(n - 1):
            f0, f1 = f1, f0 + f1
        
        return f1
```

從前一階或兩階