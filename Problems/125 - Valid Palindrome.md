---
tags:
  - string
  - twoPointers
Difficulty Level: Easy
Rating: 
Need Review: false
Origin: LC 125
First: April 7, 2025 4:59 PM
Watch Solution: false
---

# 125. Valid Palindrome

[Link](https://leetcode.com/problems/valid-palindrome/description/?envType=study-plan-v2&envId=top-interview-150)

**Topics**: String, Two Pointers
這次嘗試不要額外的空間，不要用新的array來存這些轉變完的字母，但是不能直接用```abs(ord(s[l]) - ord(s[r]))``` ，因為會有數字0 ~ 9 ，字母P跟數字0 和A , a 一樣差32 邪惡。


```python 
class Solution:
    def isPalindrome(self, s: str) -> bool:
        n = len(s)
        r = len(s) - 1
        l = 0
        while l <= r:
            while l <= n - 1 and not s[l].isalnum():
                l += 1
            while r >= 0 and not s[r].isalnum():
                r -= 1
            
            if l <= n - 1 and r >= 0:
                al = chr(ord(s[l]) + 32) if s[l] in ascii_uppercase else s[l]
                ar = chr(ord(s[r]) + 32) if s[r] in ascii_uppercase else s[r]
                
                if al != ar:
                    return False
            l += 1
            r -= 1
        
        return True
```
