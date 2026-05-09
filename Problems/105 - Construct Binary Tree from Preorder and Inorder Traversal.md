---
tags:
  - binaryTree
  - divideAndConquer
  - tree
Difficulty Level: Medium
Rating: 
Need Review: true
Origin: LC 105
First: August 6, 2025 4:01 PM
Watch Solution: false
---

# 105. Construct Binary Tree from Preorder and Inorder Traversal

**Topics**: Binary Tree, Divide and Conquer, Tree

## Notes

inorder ：root 左邊是左子樹 root 右邊是右 所以找到preOrder [0] 在裡面排第幾就可以把問題切成左右子樹了O(n**2) → 優化 O(n)

