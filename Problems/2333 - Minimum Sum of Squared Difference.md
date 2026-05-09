---
tags:
  - binarySearch
  - greedy
  - sorting
Difficulty Level: Medium
Rating: 2011
Need Review: true
Origin: LC 2333
First: September 20, 2025 12:53 PM
Watch Solution: false
---

# 2333. Minimum Sum of Squared Difference

**Topics**: Binary Search, Greedy, Sorting

## Notes

活用餘數以及尾端加入0 是關鍵，貪心的把所有的數字變小→把選中的變成跟下一個一樣大 如果不夠的話，就善用divmod ，把cnt %k 個變小k%cnt + 1 個 剩下的變小k%cnt

