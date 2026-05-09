---
tags:
  - array
  - dp
  - slidingWindow
Difficulty Level: Medium
Rating: 2005
Need Review: true
Origin: LC 1888
First: September 18, 2025 6:37 PM
Watch Solution: true
---

# 1888. Minimum Number of Flips to Make the Binary String Alternating

[Link](https://leetcode.com/problems/minimum-number-of-flips-to-make-the-binary-string-alternating/description/)

**Topics**: Array, DP, Sliding Window

## Notes

滑動窗口題！關鍵是：用s[i] ≠ i %2 來看，還有用 cnt, n - cnt 來看 （看是全部轉成現在 或是轉成反的 這種感覺）

