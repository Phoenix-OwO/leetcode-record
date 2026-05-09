---
tags:
  - bfs
  - math
Difficulty Level: Medium
Rating: 2137
Need Review: true
Origin: LC 3629
First: July 27, 2025 8:28 PM
Watch Solution: false
---

# 3629. Minimum Jumps to Reach End via Prime Teleportation

[Link](https://leetcode.com/problems/minimum-jumps-to-reach-end-via-prime-teleportation/)

**Topics**: BFS, Math

## Notes

就是BFS。

關鍵是預處理好每個數的質因數、看完一個質數之後把它從dict 刪掉（預防後面重複看）、往前往後都可以走(i+1, i-1)

不知道為什麼想到 [[3715 - Sum of Perfect Square Ancestors]] 都是質數的題目，把他們連起來好了。