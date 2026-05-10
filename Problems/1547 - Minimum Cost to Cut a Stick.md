---
tags:
  - array
  - dp
Difficulty Level: Hard
Rating: 2116
Need Review: true
Origin: LC 1547
First: June 19, 2025 7:45 PM
Watch Solution: false
---

# 1547. Minimum Cost to Cut a Stick

**Topics**: Array, DP

## Notes

區間dp 實作細節多，dp初始為0（小心），即使長度為2也要嘗試切割

top down 

```python
class Solution:
    def minCost(self, n: int, cuts: List[int]) -> int:
        cuts.append(0)
        cuts.append(n)
        cuts.sort()
        nCuts = len(cuts)
        
        @cache
        def dfs(i, j) -> int:
            if i == j - 1:
                return 0
            ans = inf
            for k in range(i + 1, j):
                ans = min(ans, dfs(i, k) + dfs(k, j) + cuts[j] - cuts[i])
            return ans
        
        return dfs(0, nCuts - 1)
```

bottom up 一樣從長度為2 往上推