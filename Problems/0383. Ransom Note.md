---
tags:
  - counting
  - hashTable
  - string
Difficulty Level: Easy
Rating: 
Need Review: false
Origin: LC 383
First: April 3, 2025 11:43 PM
Watch Solution: false
---

# 383. Ransom Note

[Link](https://leetcode.com/problems/ransom-note/?envType=study-plan-v2&envId=top-interview-150)

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        cntRan = Counter(ransomNote)
        cntMag = Counter(magazine)

        for k, v in cntRan.items():
            if cntMag[k] < v :
                return False
        
        return True
```
## Notes

兩個dict 最後檢查 或一個dict  ransom的用減的

0522更新：直接用counter 存兩個
