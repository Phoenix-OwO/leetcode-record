---
tags:
  - string
  - slidingWindow
  - prefixSum
  - dp
Difficulty Level:
Rating:
Need Review: false
Origin: 05/25 Daily
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/jump-game-vii/?envType=daily-question&envId=2026-05-25)
我用差分的解法，對於每一個index，首先確認這個可不可以抵達，如果可以，我們就用它去更新以他出發可以抵達的最右邊跟最左邊（+1, -1 的做法）
最後回傳的是最後一個index 可不可以到
也可以用dp 跟sliding window 解，

```python
class Solution:
    def canReach(self, s: str, minJump: int, maxJump: int) -> bool:
        if s[-1] == '1':
            return False
        n = len(s)
        arr = [0] * n
        arr[0] = 1
        arr[1] = -1
        curr = 0
        for i, c in enumerate(s):
            curr += arr[i]
            if curr > 0 and s[i] == '0':
                if i + minJump <= n - 1:
                    arr[i + minJump] += 1
                if i + maxJump <= n - 2:
                    arr[i + maxJump + 1] -= 1
        return curr > 0
```

```python
class Solution:
    def canReach(self, s: str, minJump: int, maxJump: int) -> bool:
        n = len(s)

        dp = [False] * n
        dp[0] = True

        reachable = 0

        for i in range(1, n):
            # add new index entering window
            if i - minJump >= 0 and dp[i - minJump]:
                reachable += 1

            # remove old index leaving window
            if i - maxJump - 1 >= 0 and dp[i - maxJump - 1]:
                reachable -= 1

            dp[i] = (reachable > 0 and s[i] == '0')

        return dp[n - 1]
``
```