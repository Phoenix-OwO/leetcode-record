---
tags:
  - array
  - math
  - numberTheory
  - stack
Difficulty Level: Hard
Rating: 2057
Need Review: true
Origin: LC 2197
First: September 16, 2025 2:33 PM
Watch Solution: false
---

# 2197. Replace Non-Coprime Numbers in Array

[Link](https://leetcode.com/problems/replace-non-coprime-numbers-in-array/description/?envType=daily-question&envId=2025-09-16)

**Topics**: Array, Math, Number Theory, Stack

## Notes

看stack 頂端跟現在的num 有沒有公因數 有的話就要把多出來的乘上satck 頂多，要小心用while ，是因為有可能加上新的數字之後可以跟前前一個配對，比如：3, 4, 6 這種感覺

