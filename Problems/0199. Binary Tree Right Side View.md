---
tags:
  - bfs
  - binaryTree
  - dfs
  - tree
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 199
First: April 4, 2025 1:28 PM
Watch Solution: false
---

# [**199. Binary Tree Right Side View**](https://leetcode.com/problems/binary-tree-right-side-view/)

**Topics**: BFS, Binary Tree, DFS, Tree

## Notes
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        ans = []
        q = [root]

        while q:
            temp = []
            ans.append(q[-1].val)
            
            for node in q:
                if node.left:
                    temp.append(node.left)
                if node.right:
                    temp.append(node.right)
            
            q = temp
        
        return ans

```

BFS 右邊先再左邊 如果 新深度就append
2026/05/22 更新：由左到右 ，把q[-1] 加進去就好！