---
tags:
Difficulty Level: Medium
Rating: 2047
Need Review: false
Origin: LC 2948
First: October 17, 2025 4:05 PM
Watch Solution: false
---

# 2948. Make Lexicographically Smallest Array by Swapping Elements

## Notes

我只想到union find，靈神詳解有分組討論，就是把index 跟num 一起放進去sort ，如果他們的絕對值都有≤ limit ，就代表他們可以分成一組，分完之後把他們按照順序填進去。

