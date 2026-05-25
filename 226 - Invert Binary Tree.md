---
tags:
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/invert-binary-tree/description/?envType=study-plan-v2&envId=top-interview-150)
如果有left 或有right 就要先dfs下去把左右都處理好，再回來現在的node 把它的左右互換

```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        
        def dfs(node) -> TreeNode:
            if node.left:
                node.left = dfs(node.left)
            if node.right:
                node.right = dfs(node.right)
            node.left, node.right = node.right, node.left
            return node
        
        return dfs(root)
```

