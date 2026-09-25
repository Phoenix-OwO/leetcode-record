---
tags:
  - dp
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 198
First: April 19, 2025 9:40 PM
Watch Solution: false
---

# 198. House Robber

**Topics**: DP

## Notes

遞歸和iterate都可以

遞迴式 ``` dp[i] = max(dp[i - 1], dp[i - 2] + nums[i]```
