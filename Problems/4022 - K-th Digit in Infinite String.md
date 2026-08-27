---
tags:
  - binarySearch
  - math
Difficulty Level: Medium
Rating: 1914
Need Review: true
Origin: Biweekly 189
First: 2026-08-15
Watch Solution: false
---
[link](https://leetcode.com/problems/k-th-digit-in-infinite-string/description/)
可以先做 [[400 - Nth Digit]]
他是那題的麻煩版
基本上是一樣的，唯一的差別是：可以先算出num -> 再透過把num 除以10 判斷他在哪個block -> 看他需不需要反轉 
（不要理GPT 他寫的太麻煩了）

```python
class Solution:
    def kthDigit(self, k: int) -> int:
        if k <= 9:
            return k
        k -= 9
        dig = 2

        while True:
            totalDig = dig * 9 * (10 ** (dig - 1))
            if totalDig < k:
                k -= totalDig
                dig += 1
            else:
                break
        k -= 1
        num = (k // dig) + (10 ** (dig - 1)) 
        block = num // 10
        if block % 2 == 0:
            return int(str(num)[k % dig])
        else:
            num = num - num % 10  + (9 - num % 10 )
            return int(str(num)[k % dig])

```

