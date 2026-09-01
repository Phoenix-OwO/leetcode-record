---
tags:
  - enumeration
  - counting
Difficulty Level: Easy
Rating: 1250
Need Review: false
Origin: Weekly 517
First: 2026-08-30
Watch Solution: false
---
[link](https://leetcode.com/problems/count-integers-appearing-in-a-single-block/description/)
照做 可以偷懶 two pass 很簡單
我猜也可以one pass 但懶得想

```python
class Solution:
    def countSpecialIntegers(self, nums: list[int]) -> int:
        cnt = Counter(nums)
        ans = 0
        n = len(nums)
        curr = 1
        i = 0
        if curr == cnt[nums[i]]:
            ans += 1          
        for i in range(1, n):
            if nums[i] == nums[i - 1]:
                curr += 1
            else:
                curr = 1
            if curr == cnt[nums[i]]:
                ans += 1 
        return ans
```

