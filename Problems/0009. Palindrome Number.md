---
tags:
  - math
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-22
Watch Solution: false
---
[link](https://leetcode.com/problems/palindrome-number/description/?envType=study-plan-v2&envId=top-interview-150)

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x <= 0:
            return x == 0

        digits = []

        while x > 0:
            x, r = divmod(x, 10)
            digits.append(r)
        
        l = len(digits)

        for i in range(l//2):
            if digits[i] != digits[l - 1 - i]:
                return False
        
        return True

        
```

使用divmod 把商跟餘數取出來即可，不要！轉成！string ！