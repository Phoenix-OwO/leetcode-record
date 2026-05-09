---
tags:
  - dp
  - string
Difficulty Level: Hard
Rating: 2450
Need Review: true
Origin: LC 3352
First: July 23, 2025 5:57 PM
Watch Solution: false
---

# 3352. Count K-Reducible Numbers Less Than N

[Link](https://leetcode.com/problems/count-k-reducible-numbers-less-than-n/)

**Topics**: DP, String

## Notes

數位dp! 關鍵：f[i] = f[i.bit_count()] + 1 這個不部分 提前算好所有可能 不要枚舉符合的

