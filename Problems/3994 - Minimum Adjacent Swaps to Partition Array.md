---
tags:
Difficulty Level: Medium
Rating:
Need Review: true
Origin: Biweekly 187
First: 2026-07-18
Watch Solution: true
---
[link](https://leetcode.com/problems/minimum-adjacent-swaps-to-partition-array/description/)
逆序對逆序對逆序對！！！！！
死在逆序對手裡很多次了 哭啊

> swap 次數可以直接是逆序對數量

群友格言：
1. 感覺把題單逆序對那邊做完就好了？
2. 常見的就是用值域BIT維護，或是把逆序對理解成二維偏序問題，在Merge Sort的過程中維護（CDQ分治）

```python
class Solution:
    def minAdjacentSwaps(self, nums: list[int], a: int, b: int) -> int:
        c0, c1, c2 = 0, 0, 0
        ans = 0
        for num in nums:
            if num < a:
                ans += c1 + c2
                c0 += 1
            elif num <= b:
                ans += c2
                c1 += 1
            else:
                c2 += 1
        return ans % (10**9 + 7)
```

