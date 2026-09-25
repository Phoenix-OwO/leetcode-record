---
tags:
  - dp
  - array
  - matrix
Difficulty Level: Hard
Rating:
Need Review: false
Origin:
First: 2026-07-12
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-consistent-columns-in-a-grid/)
很典型的dp，兩層for 迴圈，去計算col之間兩兩能不能符合規則，如果可以，就更新他的值

```python
class Solution:
    def maxConsistentColumns(self, grid: List[List[int]], limit: int) -> int:
        m = len(grid)
        n = len(grid[0])
        dp = [1] * n

        for j in range(n):
            for c in range(j):
                check = True
                for i in range(m):
                    if abs(grid[i][j] - grid[i][c]) > limit:
                        check = False
                        break
                if check:
                    dp[j] = max(dp[j], dp[c] + 1)

        return max(dp)
```

