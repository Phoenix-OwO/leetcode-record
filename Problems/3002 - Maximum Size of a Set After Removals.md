---
tags:
  - array
  - greedy
  - hashTable
Difficulty Level: Medium
Rating: 1917
Need Review: false
Origin: LC 3002
First: August 20, 2025 10:08 PM
Watch Solution: false
---

# 3002. Maximum Size of a Set After Removals

[Link](https://leetcode.com/problems/maximum-size-of-a-set-after-removals/description/)

**Topics**: Array, Greedy, Hash Table

## Notes

貪婪地取元素 最後nums1 counter + nums2 counter 長度減掉交集，最後再扣掉（1 還沒減 + 2還沒減 - 重疊） 因為減在重疊裡面就不用扣前面

