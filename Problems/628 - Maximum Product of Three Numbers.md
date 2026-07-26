---
tags:
  - array
  - math
  - sorting
Difficulty Level: Easy
Rating:
Need Review: false
Origin: 07/26 Daily
First: 2026-07-26
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-product-of-three-numbers/?envType=daily-question&envId=2026-07-26)
照做 一步一步算出最大的三個數字相乘（沿路紀錄並更新一個數字的、兩個數字的）


```python
class Solution:
    def maximumProduct(self, nums: List[int]) -> int:
        oneMax, oneMin = -inf, inf
        twoMax, twoMin = -inf, inf
        ans = -inf
        
        for i, num in enumerate(nums):
            if i >= 2:
                ans = max(twoMax * num, twoMin * num, ans)
            if i >= 1:
                twoMax = max(oneMax * num, oneMin * num, twoMax)
                twoMin = min(oneMax * num, oneMin * num, twoMin)
            oneMax = max(oneMax, num)
            oneMin = min(oneMin, num)
        return ans
```

