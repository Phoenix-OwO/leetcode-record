---
tags:
  - array
  - greedy
  - hashTable
  - sorting
Difficulty Level: Hard
Rating: 2221
Need Review: true
Origin: LC 2561
First: August 7, 2025 12:02 PM
Watch Solution: true
---

# 2561. Rearranging Fruits

[Link](https://leetcode.com/problems/rearranging-fruits/description/?envType=daily-question&envId=2025-08-02)

**Topics**: Array, Greedy, Hash Table, Sorting

## Notes

一開始看成讓兩邊相加是一樣，結果是每個元素都一樣，靈神的思路：每次都是大→小 小→大 這樣換，可以有中介元素（特別小 之類的）負責擔任被換的，A→ B, B→ A 換回來

