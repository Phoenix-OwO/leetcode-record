---
tags:
Difficulty Level: Medium
Rating: 1776
Need Review: false
Origin: Weekly 500
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-cost-to-move-between-indices/description/)


```python
class Solution:
    def minCost(self, nums: list[int], queries: list[list[int]]) -> list[int]:
        n = len(nums)
        closet = [0] * n
        closet[0] = 1
        closet[-1] = n - 2
        for i in range(1, n - 1):
            if nums[i] - nums[i - 1] <= nums[i + 1] - nums[i]:
                closet[i] = i - 1
            else:
                closet[i] = i + 1
        pre = [0] * (n + 1)
        post = [0] * (n + 1)
        for i in range(1, n):
            pre[i + 1] = pre[i] + 1 if closet[i - 1] == i else pre[i] + abs(nums[i] - nums[i - 1])
        for i in range(n - 2, -1, -1):
            post[i] = post[i + 1] + 1 if closet[i + 1] == i else post[i + 1] + abs(nums[i + 1] - nums[i])
        # print(closet)
        # print(pre)
        # print(post)
        ans = []
        for s, e in queries:
            if s <= e:
                ans.append(pre[e + 1] - pre[s + 1])
            else:
                ans.append(post[e] - post[s])
        return ans
            
```

