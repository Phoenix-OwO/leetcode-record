---
tags:
  - array
  - dp
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/?envType=study-plan-v2&envId=top-interview-150)

更新前面的最小值，要注意是先更新答案再更新global minimum

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        ans = 0
        minP = inf 

        for i, x in enumerate(prices):
            ans = max(ans, x - minP)
            minP = min(minP, x)
        
        return ans
```

