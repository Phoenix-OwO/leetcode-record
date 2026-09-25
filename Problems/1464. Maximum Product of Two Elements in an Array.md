---
tags:
  - array
  - sorting
  - heap
Difficulty Level: Easy
Rating: 1121
Need Review: false
Origin: 07/27 Daily
First: 2026-07-27
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/description/?envType=daily-question&envId=2026-07-27)
easy 題，沒什麼好說的，姑且是用了一個時間O(n) 空間O(1) 的解法

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        num1, num2 = -inf, -inf
        for num in nums:
            if num >= num1:
                num1, num2 = num, num1
            elif num > num2:
                num2 = num
        return (num1 - 1) * (num2 - 1)
```

