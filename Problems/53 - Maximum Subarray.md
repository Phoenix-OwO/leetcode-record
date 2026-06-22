---
tags:
  - array
  - dp
  - divideAndConquer
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 53
First: March 28, 2025 3:49 PM
Watch Solution: false
---

# 53. Maximum Subarray

[Link](https://leetcode.com/problems/maximum-subarray/description/)

**Topics**: Array, DP, Divide and Conquer

## Notes

Kadane’s Algorithm 題 這個真的很常用到

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        ans = -inf
        curr = 0
        for num in nums:
            curr += num
            ans = max(curr, ans)
            if curr < 0:
                curr = 0
        return ans

```



