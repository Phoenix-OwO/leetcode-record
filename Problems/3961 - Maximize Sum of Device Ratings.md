---
tags:
  - sorting
  - greedy
  - matrix
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/maximize-sum-of-device-ratings/description/)

規定是可以把一列的其中一個unit 丟到另外一列，因為算分方法是抓該列最小的，所以把最小的塞給別人最划算，最理想 -> 大家把最小值都塞給一個衰鬼

當最小的塞給別人之後他的最小值就是原先第二小的值了，所以決定衰鬼的方法就是，找出誰擁有最小的第二小的值（unit[i][1]），他就是那個選中的一列。

```python
class Solution:
    def maxRatings(self, units: List[List[int]]) -> int:
        m = len(units)
        n = len(units[0])
        
        if n == 1:
            return sum(units[i][0] for i in range(m))

        s = 0
        minS = inf
        small = inf
        for i in range(m):
            units[i] = sorted(units[i])
            s += units[i][1]
            small = min(small, units[i][0])
            minS = min(minS, units[i][1])

        return s + small - minS
        
```

