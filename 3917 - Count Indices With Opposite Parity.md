---
tags:
Difficulty Level: Easy
Rating: 1198
Need Review: false
Origin: Weekly 500
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/count-indices-with-opposite-parity/description/)

```python
class Solution:
    def countOppositeParity(self, nums: list[int]) -> list[int]:
        cnt = Counter([num % 2 for num in nums])
        n = len(nums)
        ans = [0] * n
        for i, x in enumerate(nums):
            cnt[x % 2] -= 1
            ans[i] = cnt[(x + 1) % 2]
        return ans
```

