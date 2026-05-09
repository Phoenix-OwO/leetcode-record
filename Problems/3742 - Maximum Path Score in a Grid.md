---
tags:
  - dp
  - matrix
Difficulty Level: Medium
Rating: 1804
Need Review: true
Origin: LC 3742
First: May 2, 2026 6:57 PM
Watch Solution: false
---

# 3742. Maximum Path Score in a Grid

[Link](https://leetcode.com/problems/maximum-path-score-in-a-grid/description/?envType=daily-question&envId=2026-05-02)

**Topics**: DP, Matrix

## Notes

開邊界要小心，array 可以開到k + 2, m + 1, n + 1 這樣就不用特判，此外可以滾掉m ( k從後往前更新）

