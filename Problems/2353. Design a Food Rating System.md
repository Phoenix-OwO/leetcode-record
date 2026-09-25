---
tags:
  - design
  - hashTable
  - heap(priorityQueue)
Difficulty Level: Medium
Rating: 1781
Need Review: false
Origin: LC 2353
First: September 17, 2025 1:25 PM
Watch Solution: false
---

# 2353. Design a Food Rating System

[Link](https://leetcode.com/problems/design-a-food-rating-system/description/?envType=daily-question&envId=2025-09-17)

**Topics**: Design, Hash Table, Heap (Priority Queue)

## Notes

懶刪除堆！我們沒辦法直接刪，所以就先不管 把現在的值存起來，如果堆頂端的值=我們存好的值，代表他valid 可以回傳， 如果不等於的話代表他是過期資料，所以就丟掉

