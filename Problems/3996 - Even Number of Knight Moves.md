---
tags:
  - bfs
  - matrix
Difficulty Level: Easy
Rating:
Need Review: false
Origin: Weekly 511
First: 2026-07-19
Watch Solution: false
---
[link](https://leetcode.com/problems/even-number-of-knight-moves/description/)

```python
class Solution:
    def canReach(self, start: list[int], target: list[int]) -> bool:
        visited = [[False for _ in range(8)] for _ in range(8)]
        direc = [(1, 2), (2, 1), (2, -1), (1, -2), (-1, -2), (-2, -1), (-2, 1), (-1, 2)]

        q = deque([(start[0], start[1], 0)])

        while q:
            x, y, d = q.popleft()
            for dx, dy in direc:
                if 0 <= x + dx < 8 and 0 <= y + dy < 8 and not visited[y + dy][x + dx]:
                    if x + dx == target[0] and y + dy == target[1]:
                        return (d + 1) % 2 == 0
                    q.append((x + dx, y + dy, d + 1))
        return False
        
```

