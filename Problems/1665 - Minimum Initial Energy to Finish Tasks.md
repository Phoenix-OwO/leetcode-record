---
tags:
  - greedy
  - sorting
  - array
Difficulty Level: Hard
Rating: 1900
Need Review: false
Origin: 05/12 Daily
First: 2026-05-12
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-initial-energy-to-finish-tasks/?envType=daily-question&envId=2026-05-14)

關鍵：按照剩下的能量（開始能量減用掉的能量）
因為這個能量一定是被浪費掉的，沒辦法被後面的人利用，所以由剩下的多到少排。

```python
class Solution:
    def minimumEffort(self, tasks: List[List[int]]) -> int:
        tasks.sort(key = lambda x: x[1] - x[0], reverse = True)
        ans = 0
        curr = 0
        for a, m in tasks:
            if curr < m:
                ans += m - curr
                curr = m
            curr -= a
        return ans
```

