---
tags:
  - tree
  - binaryTree
  - dfs
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Weekly 511
First: 2026-07-19
Watch Solution: false
---
[link](https://leetcode.com/problems/count-dominant-nodes-in-a-binary-tree/description/)
就是dfs，從下往上傳每個node 以降的最大值，如果今天這個值等於node.val，我們就回傳他。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def countDominantNodes(self, root: TreeNode | None) -> int:
        self.cnt = 0
        
        def dfs(node) -> currMax:
            currMax = node.val 
            if node.left:
                currMax = max(dfs(node.left), currMax)
            if node.right:
                currMax = max(dfs(node.right), currMax)
            if currMax == node.val:
                self.cnt += 1
            return currMax

        dfs(root)

        return self.cnt
```

