---
tags:
  - bitManipulation
  - bitmask
  - dp
Difficulty Level: Hard
Rating: 2185
Need Review: true
Origin: LC 943
First: July 28, 2025 4:37 PM
Watch Solution: true
---

# 943. Find the Shortest Superstring

[Link](https://leetcode.com/problems/find-the-shortest-superstring/description/)

**Topics**: Bit Manipulation, BitMask, DP

## Notes

很煩題 前處理算重疊、三層for 迴圈 mask → i（在mask 裡的） → j （新的準備加進來的）時間O(n*2**n)

