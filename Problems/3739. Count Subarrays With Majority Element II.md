---
tags:
  - binarySearch
  - hashTable
  - prefixSum
  - segmentTree
Difficulty Level: Hard
Rating: 2089
Need Review: true
Origin: LC 3739
First: November 13, 2025 3:18 PM
Watch Solution: true
---

# 3739. Count Subarrays With Majority Element II

[Link](https://leetcode.com/problems/count-subarrays-with-majority-element-ii/description/)

**Topics**: Binary Search, Hash Table, Prefix Sum, Segment Tree

## Notes

binary search就可以做，num == target → curr + 1, num ≠ target → curr - 1，然後我們去前綴堆裡面找< curr 的值就好，用SortedList 就解決了！

