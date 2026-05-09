---
tags:
  - dp
  - slidingWindow
Difficulty Level: Medium
Rating: 2350
Need Review: true
Origin: LC 837
First: August 18, 2025 2:42 PM
Watch Solution: true
---

# 837. New 21 Game

[Link](https://leetcode.com/problems/new-21-game/description/?envType=daily-question&envId=2025-08-17)

**Topics**: DP, Sliding Window

## Notes

從後往前推，f[i]代表從i分開始到達≤ n結束的機率，當 k≤ i ≤ n 是1 , > n 是0，f[i] 就是 f[i+1], f[i+2] … f[i+maxP] 加起來除以maxP ，很聰明又優雅的講法

