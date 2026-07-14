---
tags:
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Weekly 510
First: 2026-07-12
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-total-cost-to-process-all-elements/)
貪心（？）小陷阱題

忘記% MOD 還有沒注意到num 的範圍吃了兩次罰時。

關鍵：num 有可能比k大很多，所以不能一次一次慢慢加，要直接看我們需要加幾次k。

因為每加一次k 的cost 會上升e.g. 加三次就是1 2 3 ，這邊可以用等差數列處理。

```python
class Solution:
    def minimumCost(self, nums: list[int], k: int) -> int:
        c = 0
        currCost = 1
        rem = k
        MOD = 10 **9 + 7
        for num in nums:
            if rem < num:
                times = ceil((num - rem)/k)
                rem += k * times
                c += ((currCost + currCost + times - 1) * times) // 2
                c %= MOD
                currCost += times
            rem -= num
        return c % MOD
```

