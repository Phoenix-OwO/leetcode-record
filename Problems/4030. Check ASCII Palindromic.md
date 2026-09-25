---
tags:
  - string
  - enumeration
Difficulty Level: Easy
Rating: 1165
Need Review: false
Origin: Weekly 516
First: 2026-08-23
Watch Solution: false
---
[link](https://leetcode.com/problems/check-ascii-palindromic/description/)
照做即可題

```python
class Solution:
    def isPalindromic(self, s: str) -> bool:
        binS = []
        for c in s:
            curr = '0' * (8 - len(bin(ord(c))[2:])) + bin(ord(c))[2:]
            binS.append(curr)
        binS = ''.join(binS)
        return binS == binS[::-1]
```

