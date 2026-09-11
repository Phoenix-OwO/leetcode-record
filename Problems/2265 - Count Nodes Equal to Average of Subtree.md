---
tags:
  - dfs
  - binaryTree
Difficulty Level: Medium
Rating: 1472
Need Review: false
Origin: Weekly 516
First: 2026-09-10
Watch Solution: false
---
[link](https://leetcode.com/problems/count-nodes-equal-to-average-of-subtree/description/?envType=daily-question&envId=2026-09-10)
普通的dfs 題目 沒啥特別的
```python
class Solution:
    def averageOfSubtree(self, root: TreeNode) -> int:
        self.ans = 0

        def countSum(node)-> int:
            l, r = 0, 0
            cntL, cntR = 0, 0
            if node.left:
                l, cntL = countSum(node.left)
            if node.right:
                r, cntR = countSum(node.right)
            if node.val == floor((l + r + node.val)/(1 + cntL + cntR)):
                self.ans += 1
            return node.val + l + r, 1 + cntL + cntR
        countSum(root)

        return self.ans
```

