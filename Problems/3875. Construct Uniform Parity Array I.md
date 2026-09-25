---
tags:
Difficulty Level: Easy
Rating: 1199
Need Review: false
Origin: 09/02 Daily
First: 2026-09-02
Watch Solution: false
---
[link](https://leetcode.com/problems/construct-uniform-parity-array-i/description/?envType=daily-question&envId=2026-09-02)
簡單來說就是看能不能組出全奇數跟全偶數的，今天如果只有一奇或一偶就不行
更新：突然發現可以直接return true 因為所有的狀況都符合 笑死

```python
class Solution:
    def uniformArray(self, nums1: list[int]) -> bool:
        cnt0, cnt1 = 0, 0
        for num in nums1:
            if num % 2 == 0:
                cnt0 += 1
            else:
                cnt1 += 1
        checkOdd, checkEven = True, True
        for num in nums1:
            if (num % 2 == 0 and cnt1 == 0):
                checkOdd = False
            if num % 2 == 1 and cnt0 == 0:
                checkEven = False 
        return checkOdd or checkEven 
```

