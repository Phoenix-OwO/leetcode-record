---
tags:
  - binarySearch
  - math
  - combinatorics
Difficulty Level: Medium
Rating: 2039
Need Review: false
Origin:
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/ugly-number-iii/description/)

l = 0, r = upper 對他們二分，至於前面有幾個數字可以用排列組合算因數的那個算法算
注意：是lcm （最小公倍數） 不是相乘

``` python
class Solution:
    def nthUglyNumber(self, n: int, a: int, b: int, c: int) -> int:
        l, r = 0, 2 * (10 **9)

        def check(i: int) -> bool:
            cnt = i // a + i // b + i // c - i // lcm(a, b) - i //lcm(a,c) - i // lcm(b, c) + i // lcm(a, b, c)
            return cnt >= n

        while l <= r:
            mid = (l + r)//2
            if check(mid):
                r = mid - 1
            else:
                l = mid + 1
        return l
```