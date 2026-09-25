---
tags:
  - array
Difficulty Level: Easy
Rating: 1250
Need Review: false
Origin: LC 3663
First: September 1, 2025 2:41 PM
Watch Solution: false
---

# 3663. Find The Least Frequent Digit

[Link](https://leetcode.com/problems/find-the-least-frequent-digit/submissions/1755525885/)

**Topics**: Array

## Notes

轉字串比較快，此外可以直接sort 就好啊，比較快int(sorted([(v, k) for k, v in Counter(str(n)).items()])[0][1])

