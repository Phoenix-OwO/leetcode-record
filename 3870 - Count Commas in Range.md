---
tags:
  - math
Difficulty Level: Easy
Rating: 1149
Need Review: false
Origin: 09/08 Daily
First: 2026-09-08
Watch Solution: false
---
[link](https://leetcode.com/problems/count-commas-in-range/description/?envType=daily-question&envId=2026-09-03)
關鍵：注意到資料範圍<10^5 
所以每個數字最多只會有一個逗號，因為從1000開始才有，於是我們可以把它扣掉前面的999
```python
class Solution:
    def countCommas(self, n: int) -> int:
        if n < 1000:
            return 0
        return n - 999
```

