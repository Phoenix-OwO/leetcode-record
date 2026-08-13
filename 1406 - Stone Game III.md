---
tags:
  - dp
Difficulty Level:
Rating:
Need Review: false
Origin: 08/05 Daily
First: 2026-08-05
Watch Solution: false
---
[link](https://leetcode.com/problems/stone-game-iii/?envType=daily-question&envId=2026-08-05)
最大化：兩個人的得分差。
stone game 好像很多都是這個套路
法一是top down 法二是bottom up

```python
class Solution:
    def stoneGameIII(self, stoneValue: List[int]) -> str:
        pre = list(accumulate(stoneValue, initial = 0))
        n = len(stoneValue)

        @cache
        def dfs(i: int) -> int:
            if i == n:
                return 0

            ans = -inf
            for s in range(i, min(n, i + 3)):
                ans = max(ans, pre[s + 1] - pre[i] - dfs(s + 1))
            return ans
        x = dfs(0)
        if x > 0:
            return 'Alice'
        elif x == 0:
            return 'Tie'
        else:
            return 'Bob'


```

```python
class Solution:
    def stoneGameIII(self, stoneValue: List[int]) -> str:

        n = len(stoneValue)
        dp = [0 for _ in range(4)]
        
        for i in range(n - 1, -1, -1):
            curr = 0
            dp[i % 4] = -inf
            for j in range(3):
                curr += stoneValue[i + j] if i + j < n else 0
                dp[i % 4] = max(dp[i % 4], curr - dp[(i + j + 1) % 4]) 
        
        if dp[0] > 0:
            return 'Alice'
        elif dp[0] == 0:
            return 'Tie'
        else:
            return 'Bob'

```
