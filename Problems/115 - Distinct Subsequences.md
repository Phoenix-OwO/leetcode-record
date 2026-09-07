---
tags:
  - dp
  - string
Difficulty Level: Hard
Rating: 
Need Review: true
Origin: LC 115
First: May 23, 2025 9:48 PM
Watch Solution: false
---

# [**115. Distinct Subsequences**](https://leetcode.com/problems/distinct-subsequences/)

**Topics**: DP, String

## Notes

有O(n)空間的優化，和1143很接近，只差在1143取max 115用加的
底下是有空間優化的版本，由後往前羹新就好。

```python
class Solution:
    def numDistinct(self, s: str, t: str) -> int:
        n = len(t)
        dp = [0] * (n + 1)
        dp[0] = 1
        for c in s:
            for i in range(n - 1, -1, -1):
                if c == t[i]:
                    dp[i + 1] += dp[i]
        return dp[-1]

```