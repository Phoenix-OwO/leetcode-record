---
tags:
  - backtracking
  - bitManipulation
  - bitmask
  - dp
Difficulty Level: Medium
Rating: 1886
Need Review: true
Origin: LC 2305
First: July 15, 2025 9:26 PM
Watch Solution: true
---

# 2305. Fair Distribution of Cookies

[Link](https://leetcode.com/problems/fair-distribution-of-cookies/description/)

**Topics**: Backtracking, Bit Manipulation, BitMask, DP

## Notes

狀壓dp、由大到小枚舉所有子級的做法：s = (s - 1) & j

