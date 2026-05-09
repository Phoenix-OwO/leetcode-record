---
tags:
  - bitManipulation
  - math
Difficulty Level: Hard
Rating: 
Need Review: false
Origin: LC 3782
First: December 21, 2025 11:42 AM
Watch Solution: false
---

# 3782. Last Remaining Integer After Alternating Deletion Operations

[Link](https://leetcode.com/problems/last-remaining-integer-after-alternating-deletion-operations/description/)

**Topics**: Bit Manipulation, Math

## Notes

在刪除數字時，會刪掉所有尾數和他不一樣的數字，一次大約會刪掉一半 ->想到應該可以透過right shift 左右界來實作。 要小心當另外一端點會被此操作刪掉時，要記得把端點像內側移。

