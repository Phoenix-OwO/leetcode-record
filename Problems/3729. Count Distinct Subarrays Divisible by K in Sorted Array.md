---
tags:
  - array
  - hashTable
  - prefixSum
Difficulty Level: Hard
Rating: 2248
Need Review: true
Origin: LC 3729
First: November 2, 2025 5:18 PM
Watch Solution: false
---

# 3729. Count Distinct Subarrays Divisible by K in Sorted Array

[Link](https://leetcode.com/problems/count-distinct-subarrays-divisible-by-k-in-sorted-array/description/)

**Topics**: Array, Hash Table, Prefix Sum

## Notes

我的解法簡單又漂亮，基於他的non decreasing 性質，我們可以知道說重複array 只發生在整條都是一樣的狀態下，所以我們要記得扣掉開頭是一樣的subarray ，用一個for 迴圈就看解決

