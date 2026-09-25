---
tags:
  - array
  - backtracking
  - bitManipulation
  - bitmask
Difficulty Level: Medium
Rating: 1995
Need Review: true
Origin: LC 1986
First: July 17, 2025 3:14 PM
Watch Solution: true
---

# 1986. Minimum Number of Work Sessions to Finish the Tasks

[Link](https://leetcode.com/problems/minimum-number-of-work-sessions-to-finish-the-tasks/description/)

**Topics**: Array, Backtracking, Bit Manipulation, BitMask

## Notes

原本想法：跟前幾題一樣用k 當成功就return k 但是TLE, 改用枚舉所有子集 如果SUM[s] < limit →  SUM[s^j] = min(, f[s]) 初始化f[0] 是0其他inf

