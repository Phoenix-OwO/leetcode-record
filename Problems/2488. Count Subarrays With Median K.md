---
tags:
  - array
  - hashTable
  - prefixSum
Difficulty Level: Hard
Rating: 1998
Need Review: true
Origin: LC 2488
First: August 7, 2025 1:13 PM
Watch Solution: false
---

# 2488. Count Subarrays With Median K

[Link](https://leetcode.com/problems/count-subarrays-with-median-k/)

**Topics**: Array, Hash Table, Prefix Sum

## Notes

注意：裡面的元素不重複！（有了這個前提就很好解），看k往左長跟往右長，如果>k跟<k的元素個數有match 答案就可以+1，實作上有一些小細節

