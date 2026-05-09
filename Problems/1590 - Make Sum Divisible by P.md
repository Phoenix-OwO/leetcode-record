---
tags:
  - hashTable
  - prefixSum
Difficulty Level: Medium
Rating: 2038
Need Review: false
Origin: LC 1590
First: October 17, 2025 3:09 PM
Watch Solution: false
---

# 1590. Make Sum Divisible by P

[Link](https://leetcode.com/problems/make-sum-divisible-by-p/description/)

**Topics**: Hash Table, Prefix Sum

## Notes

基本的前綴和題，可以先算Sum 知道我們要刪掉的餘數，接著去找說前面出現過的符合的目標，因為curr - prev = target 所以我們去找curr - target，要記得在前面加上一個pos[0] = -1 最後再判斷有沒有不小心整條刪掉的狀況。

