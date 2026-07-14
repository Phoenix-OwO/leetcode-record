---
tags:
  - enumeration
Difficulty Level: Easy
Rating:
Need Review: false
Origin: Weekly 510
First: 2026-07-12
Watch Solution: false
---
[link](https://leetcode.com/problems/number-of-elapsed-seconds-between-two-times/)

照做即可
```python
class Solution:
    def secondsBetweenTimes(self, startTime: str, endTime: str) -> int:
        h = (int(endTime[0:2]) - int(startTime[0:2])) * 3600
        m = (int(endTime[3:5]) - int(startTime[3:5])) * 60
        s = (int(endTime[6:]) - int(startTime[6:]))
        return h + m + s
```

