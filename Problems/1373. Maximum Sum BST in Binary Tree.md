---
tags:
  - bfs
  - binarySearchTree
  - binaryTree
  - dfs
  - dp
Difficulty Level: Hard
Rating: 1913
Need Review: true
Origin: LC 1373
First: July 24, 2025 3:12 PM
Watch Solution: false
---

# 1373. Maximum Sum BST in Binary Tree

[Link](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/description/)

**Topics**: BFS, Binary Search Tree, Binary Tree, DFS, DP

## Notes

用self.ans 中途抓最大 最後只傳sum of 子樹上去（如果not valid 回傳-inf 就不會再前面被抓到了）

