---
tags:
  - matrix
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Biweekly 190
First: 2026-08-29
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-bishop-moves-to-reach-target/)
檢查如果在同一個對角線上面，就可以一步就到，如果不是，但是是同個顏色的格子（黑色或白色），帶表兩步到
如果顏色不一樣，代表走不到

```python
class Solution:
    def minBishopMoves(self, source: list[int], target: list[int]) -> int:
        if (source[0] % 2) ^ (source[1] % 2) != (target[0] % 2) ^ (target[1] % 2):
            return -1
        if source[0] + source[1] == target[0] + target[1] or source[0] - source[1] == target[0] - target[1]:
            return 1
        return 2
```

