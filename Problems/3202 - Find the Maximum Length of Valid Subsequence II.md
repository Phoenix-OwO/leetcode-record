---
tags:
  - array
  - dp
Difficulty Level: Medium
Rating: 1973
Need Review: true
Origin: LC 3202
First: July 17, 2025 3:49 PM
Watch Solution: true
---

# 3202. Find the Maximum Length of Valid Subsequence II

[Link](https://leetcode.com/problems/find-the-maximum-length-of-valid-subsequence-ii/description/?envType=daily-question&envId=2025-07-17)

**Topics**: Array, DP

## Notes

兩種解法，本質：觀察到數列是交錯的。法一（直觀）：枚舉數列最後兩項 用f[x][y]存起來。法二（省空間）：for迴圈m 0~k-1，f[x] = f[m - x] + 1。

