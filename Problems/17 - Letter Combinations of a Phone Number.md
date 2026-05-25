---
tags:
  - backtracking
  - hashTable
  - string
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 17
First: April 18, 2025 11:29 PM
Watch Solution: false
---

# [**17. Letter Combinations of a Phone Number**](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

**Topics**: Backtracking, Hash Table, String


要記得把path pop掉 恢復原狀才可以看下一個digit 

```python 
key = {'2':'abc', '3':'def', '4':'ghi', '5':'jkl', '6':'mno', '7':'pqrs','8': 'tuv', '9': 'wxyz'}

class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        ans = []
        path = []
        l = len(digits)
        
        def dfs(i) -> None:
            if i == l:
                ans.append(''.join(path))
                return 
            for c in key[digits[i]]:
                path.append(c)
                dfs(i + 1)
                path.pop()
            return 
        dfs(0)
        return ans

```
