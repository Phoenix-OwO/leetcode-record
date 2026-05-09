---
tags:
  - greedy
  - sorting
  - twoPointers
Difficulty Level: Medium
Rating: 1827
Need Review: false
Origin: LC 3752
First: December 12, 2025 3:54 PM
Watch Solution: false
---

# 3752. Lexicographically Smallest Negated Permutation that Sums to Target

[Link](https://leetcode.com/problems/lexicographically-smallest-negated-permutation-that-sums-to-target/description/)

**Topics**: Greedy, Sorting, Two Pointers

## Notes

全部 - 負的*2，如果是奇數回傳0，可以證明如果target ≤ (n - 1)*n/2 的話一定可以湊得出來（重要），貪心的取，決定擺前面或是擺後面可以用雙指針

