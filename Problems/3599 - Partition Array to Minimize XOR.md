---
tags:
  - bitManipulation
  - dp
  - prefixSum
Difficulty Level: Medium
Rating: 1954
Need Review: true
Origin: LC 3599
First: August 18, 2025 6:18 PM
Watch Solution: false
---

# 3599. Partition Array to Minimize XOR

[Link](https://leetcode.com/problems/partition-array-to-minimize-xor/description/)

**Topics**: Bit Manipulation, DP, Prefix Sum

## Notes

複習時記得試試bottom-up 1.當currXor > res 時結果不會更小，直接剪枝continue 2. for迴圈上界可以針對k跟currCut 剪，因為我們至少要留下(k-1-currCut個元素給後面的切)

