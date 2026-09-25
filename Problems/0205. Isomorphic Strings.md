---
tags:
  - hashTable
  - string
Difficulty Level: Easy
Rating:
Need Review: true
Origin: LC 205
First: April 3, 2025 11:52 PM
Watch Solution: false
---

# [**205. Isomorphic Strings**](https://leetcode.com/problems/isomorphic-strings/)

**Topics**: Hash Table, String

## Notes

小心！一一對應 我說到這
以後的我請看到並想起來

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        alpha = {}
        alpha2 = set()
        
        for i, c in enumerate(s):
            if c in alpha and alpha[c] != t[i]:
                return False
            elif c not in alpha and t[i] in alpha2:
                return False
            else:
                alpha[c] = t[i]
                alpha2.add(t[i])
        return True

```

0522更新：
又掉進去了：）
不能對到同一個字母 像是b -> b, d -> b