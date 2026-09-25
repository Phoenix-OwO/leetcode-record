---
tags:
  - bitManipulation
  - recursion
  - simulation
Difficulty Level: Easy
Rating: 1288
Need Review: true
Origin: LC 3304
First: July 4, 2025 11:18 AM
Watch Solution: false
---

# 3304. Find the K-th Character in String Game I

[Link](https://leetcode.com/problems/find-the-k-th-character-in-string-game-i/description/?envType=daily-question&envId=2025-07-04)

**Topics**: Bit Manipulation, Recursion, Simulation

## Notes

要想到bit manipulation 很難欸, chr(ord('a') + ((k-1).bit_count())%26)

