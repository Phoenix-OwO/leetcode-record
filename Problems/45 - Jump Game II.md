---
tags:
  - array
  - greedy
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 45
First: May 21, 2025 2:58 PM
Watch Solution: false
---

# 45. Jump Game II

**Topics**: Array, Greedy

## Notes

貪婪地找出現在這格可以跳到得最遠的地方 但要小心index 超過去的狀況

[link](https://leetcode.com/problems/jump-game-ii/description/?envType=study-plan-v2&envId=top-interview-150)
這一題的關鍵是：我們站在格子上的時候，由後往前更新所有可以踩到的格子，如果說這個格子已經被前面的更新過了，我們就break 迴圈，因為這個格子以左全都被更新過了，我們不需要浪費時間去更新他。




```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        n = len(nums)
        if n == 1 :
            return 0
        steps = [inf] * n
        steps[0] = 0

        for i, x in enumerate(nums):
            right = min(n - 1, i + x)
            if right == n - 1:
                return steps[i] + 1
            while right > i:
                if steps[right] != inf:
                    break
                steps[right] = steps[i] + 1
                right -= 1
        
        return steps[n - 1]
```

