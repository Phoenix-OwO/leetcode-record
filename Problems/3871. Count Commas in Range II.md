---
tags:
Difficulty Level: Medium
Rating: 1380
Need Review: false
Origin: 09/09 Daily
First: 2026-09-09
Watch Solution: false
---
[link](https://leetcode.com/problems/count-commas-in-range-ii/submissions/2136219430/?envType=daily-question&envId=2026-09-03)
昨天那題的延伸，差別在於他的範圍是1^15 ，這樣的話就會遇到一個數字有大於一個逗號，所以就只能想其他算法。
於是就變成這個while 的寫法

```python
class Solution:
    def countCommas(self, n: int) -> int:
        ans = 0
        curr = 999
        while n > curr:
            ans += n - curr
            curr = curr * 1000 + 999

        return ans
```

