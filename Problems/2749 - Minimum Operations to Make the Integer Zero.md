---
tags:
  - bitManipulation
  - enumeration
Difficulty Level: Medium
Rating: 2132
Need Review: true
Origin: LC 2749
First: September 5, 2025 2:13 PM
Watch Solution: true
---

# 2749. Minimum Operations to Make the Integer Zero

[Link](https://leetcode.com/problems/minimum-operations-to-make-the-integer-zero/description/?envType=daily-question&envId=2025-09-05)

**Topics**: Bit Manipulation, Enumeration

## Notes

這題很酷，腦筋急轉彎，不斷地把num1 減掉num2 ，減i次時時候看num1能不能被湊出來，基本上只要n ≥ i ≥ bit count 就可以了 （如果< bit count 的話i不夠用）

