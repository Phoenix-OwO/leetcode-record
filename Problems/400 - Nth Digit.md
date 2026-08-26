---
tags:
  - math
  - binarySearch
Difficulty Level:
Rating:
Need Review: false
Origin:
First: 2026-08-21
Watch Solution: false
---
[link](https://leetcode.com/problems/nth-digit/description/)
關鍵步驟：看出是幾位數-> 看出是第幾個數字 -> 看出是第幾位
這題雖然範圍到2 的31 次，但其實經過觀察，會發現因為每個位數的數字很多，所以上漲得很快。
比如2 位數，就有```2 * 9 * 10**1 ```這麼多個digit 
（我一開始寫的時候，沒想到要乘以2 所以錯了QQ



```python
class Solution:
    def findNthDigit(self, n: int) -> int:
        if n < 10:
            return n
        d = 2
        n -= 9
        while True:
            digits = d * 9 * 10 ** (d - 1)
            if digits >= n:
                break
            n -= digits 
            d += 1

        n -= 1
        num = (n // d) + (10 ** (d - 1) ) 
        dig = n % d
        
        return int(str(num)[dig])

```

