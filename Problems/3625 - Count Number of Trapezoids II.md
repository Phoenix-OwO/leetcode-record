---
tags:
  - array
  - geometry
  - hashTable
Difficulty Level: Hard
Rating: 2643
Need Review: true
Origin: LC 3625
First: December 11, 2025 10:33 PM
Watch Solution: true
---

# 3625. Count Number of Trapezoids II

[Link](https://leetcode.com/problems/count-number-of-trapezoids-ii/description/?envType=daily-question&envId=2025-12-11)

**Topics**: Array, Geometry, Hash Table

## Notes

要扣掉平行四邊形，因為會被算兩次，可以用中點去看，此外學到了defaultdict 新用法：defaultdict(lambda: defaultdict(int))

