---
tags:
  - greedy
  - heap(priorityQueue)
  - string
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 3781
First: December 21, 2025 11:41 AM
Watch Solution: false
---

# 3781. Maximum Score After Binary Swaps

[Link](https://leetcode.com/problems/maximum-score-after-binary-swaps/description/)

**Topics**: Greedy, Heap (Priority Queue), String

## Notes

每遇到一個1 可以選index<= 它的最大數字。 用一個hq紀錄先前出現過的數字，遇到1就heappop

