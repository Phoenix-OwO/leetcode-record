---
tags:
Difficulty Level: Hard
Rating:
Need Review: false
Origin: Biweekly 187
First: 2026-07-18
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-cost-to-convert-string-iii/description/)
dp題，算是典型吧我覺得。

```python
class Solution:
    def minCost(self, source: str, target: str, rules: list[list[str]], costs: list[int]) -> int:
        n = len(source)
        dp = [inf] * (n + 1)
        dp[0] = 0
        
        def check(si, ir):
            pattern = rules[ir][0]
            rep = rules[ir][1]
            cnt = 0
            for j in range(len(pattern)):
                if pattern[j] == '*':
                    cnt += 1
                if (source[si + j] != pattern[j] and pattern[j] != '*') or target[si + j] != rep[j]:
                    return False, False
            return True, cnt

        for i in range(n):
            if dp[i] == inf:
                continue
            if source[i] == target[i]:
                dp[i + 1] = min(dp[i + 1], dp[i])
            
            for ir, r in enumerate(rules):                
                if i + len(r[0]) <= n:
                    c1, c2 = check(i, ir)
                    if c1:
                        dp[i + len(r[0])] = min(dp[i + len(r[0])], dp[i] + costs[ir] + c2)
                
                    
        return dp[-1] if dp[-1] != inf else -1
```

