---
tags:
  - bitManipulation
  - greedy
  - prefixSum
Difficulty Level: Medium
Rating: 1912
Need Review: true
Origin: LC 2680
First: August 20, 2025 4:14 PM
Watch Solution: false
---

# 2680. Maximum OR

[Link](https://leetcode.com/problems/maximum-or/description/)

**Topics**: Bit Manipulation, Greedy, Prefix Sum

## Notes

two pass, 一次算suffix or 的結果 第二次直接go through 每一個數字：算它<<k 跟post 跟pre 的最大值→更新prefix or

