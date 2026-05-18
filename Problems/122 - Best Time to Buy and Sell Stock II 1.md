---
tags:
  - array
  - dp
  - greedy
Difficulty Level: Medium
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/?envType=study-plan-v2&envId=top-interview-150)

[[121 - Best Time to Buy and Sell Stock]] 只能買賣一次的滿本

這一題可以買賣無數次，所以貪婪地選取有賺錢的區段，亦即只要有比前一個大，我們就買賣，賺取這一段的價差。


```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        ans = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i - 1]:
                ans += prices[i] - prices[i - 1]
        return ans
```

