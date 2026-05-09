---
tags:
  - array
  - hashTable
  - prefixSum
  - sorting
Difficulty Level: Medium
Rating: 1969
Need Review: true
Origin: LC 1943
First: August 20, 2025 3:43 PM
Watch Solution: true
---

# 1943. Describe the Painting

[Link](https://leetcode.com/problems/describe-the-painting/description/)

**Topics**: Array, Hash Table, Prefix Sum, Sorting

## Notes

什麼時候用差分？差分！學到了，對每個l, r, color 紀錄 碰到l 要加上color ，碰到r之後要減掉color （因為是開區間，所以在r 減，閉區間就要在r+1減掉），最後sort 所有特別的點，去計算每一個區間的值

