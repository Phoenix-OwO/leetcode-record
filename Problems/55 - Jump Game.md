---
tags:
  - dp
  - greedy
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/jump-game/?envType=study-plan-v2&envId=top-interview-150)

對於每一個index ，我們先確認他是否能被前面的格子踩到，如果否，則代表我們後面也都走不到了。
之後再來更新目前的格子可以踩到的最遠的格子。




```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        n = len(nums)
        l = 0
        currMax = 0
        for i, x in enumerate(nums):
            if i > currMax:
                return False
            currMax = max(currMax, i + x)
            if currMax >= n - 1:
                return True
        return True
            
```



Jump Game 有一整系列ㄛ : )
[[45 - Jump Game II]]
[[1306 - Jump Game III]]
[[1345 - Jump Game IV]]
[[1871 - Jump Game VII]]
[[3660 - Jump Game IX]]
