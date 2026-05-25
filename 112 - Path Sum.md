---
tags:
  - dfs
  - bfs
  - binaryTree
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/path-sum/description/?envType=study-plan-v2&envId=top-interview-150)

如果這個node 是leaf ，這個時候就回傳currSum == targetSum，如過不是leaf 的話不能這樣傳，因為他要求的是從root 到leaf ，不能中途回頭。

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        
        def dfs(node, currSum) -> bool:
            currSum += node.val
            check = False

            if node.left:
                check |= dfs(node.left, currSum)
            if node.right:
                check |= dfs(node.right, currSum)
            
            return currSum == targetSum if (not node.right and not node.left) else check
        
        return dfs(root, 0)

```

