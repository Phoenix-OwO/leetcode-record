---
tags:
  - enumeration
  - string
Difficulty Level: Hard
Rating: 2010
Need Review: true
Origin: LC 3614
First: July 14, 2025 1:24 PM
Watch Solution: true
---

# 3614. Process String with Special Operations II

[Link](https://leetcode.com/problems/process-string-with-special-operations-ii/description/)

**Topics**: Enumeration, String

## Notes

正難則反 想好最後一步就可以一路往前推了


```python
class Solution:
    def processStr(self, s: str, k: int) -> str:
        n = len(s)
        res = [0] * n
        curr = 0
        
        for i, c in enumerate(s):
            if c == '*' and curr > 0:
                curr -= 1
            elif c == '#':
                curr *= 2
            elif c != '%' and c != '*':
                curr += 1
            res[i] = curr
        
        if k >= res[-1]:
            return '.'
        
        for i in range(n - 1, -1, -1):
            if s[i] == '#':
                m = res[i]//2
                if k >= m:
                    k -= m
            elif s[i] == '%':
                k = res[i] - k - 1
            elif s[i] != '*' and k == res[i] - 1:
                return s[i]
```