---
tags:
  - dp
Difficulty Level: Hard
Rating: 1786
Need Review: false
Origin: 08/10 Daily
First: 2026-08-10
Watch Solution: false
---
[link](https://leetcode.com/problems/stone-game-iv/?envType=daily-question&envId=2026-08-10)
就是dp 題，本來想說要記錄i 跟turn 是誰，但其實不重要，
可以直接跟下一個not，就是下一個人不能贏，這個人才有機會贏，這樣的感覺。


```python
class Solution:
    def winnerSquareGame(self, n: int) -> bool:
        
        @cache
        def dfs(i) -> bool:
            ans = False
            if i == ceil(sqrt(i)) ** 2:
                return True
            for j in range(ceil(sqrt(i)) - 1, 0 , -1):
                ans = ans or not dfs(i - j ** 2)
                if ans == True:
                    return True
            return ans
        
        return dfs(n)
```

