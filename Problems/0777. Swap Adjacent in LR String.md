---
tags:
  - string
  - twoPointers
Difficulty Level: Medium
Rating: 1938
Need Review: true
Origin: LC 777
First: October 14, 2025 2:57 PM
Watch Solution: false
---

# 777. Swap Adjacent in LR String

[Link](https://leetcode.com/problems/swap-adjacent-in-lr-string/description/)

**Topics**: String, Two Pointers

## Notes

腦筋急轉彎題，要注意到L可以從後面穿越X、R可以從前往後走，X不重要，我們要注意的是在result裡的L有沒有在start的L右邊，R反之。要用two pointer 的原因是我們其實不在乎x 只在意L, R 的相對關係，所以可以用two pointer

