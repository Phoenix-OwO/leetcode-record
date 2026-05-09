---
tags:
  - monotonicQueue
  - numberTheory
  - slidingWindow
Difficulty Level: Medium
Rating: 2200
Need Review: true
Origin: LC 3589
First: June 25, 2025 3:03 PM
Watch Solution: false
---

# 3589. Count Prime-Gap Balanced Subarrays

[Link](https://leetcode.com/problems/count-prime-gap-balanced-subarrays/description/sli)

**Topics**: Monotonic Queue, Number Theory, Sliding Window

## Notes

埃氏篩、sliding window要小心左端點：右邊至少要有兩個質數，所以可以追蹤last 跟last2 這兩個質數的位置（一開始初始化成-1)

