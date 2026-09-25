---
tags:
  - array
  - matrix
  - simulation
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 289
First: April 8, 2025 8:33 PM
Watch Solution: false
---

# 289. Game of Life

[Link](https://leetcode.com/problems/game-of-life/description/?source=submission-ac)

```python 
class Solution:
    def gameOfLife(self, board: List[List[int]]) -> None:
        direc = [(-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 1), (1, -1), (1, 0), (1, 1)]
        m = len(board)
        n = len(board[0]) 
        
        for i in range(m):
            for j in range(n):
                cnt = 0
                for di, dj in direc:
                    if 0 <= i +di < m and 0 <= j + dj < n :
                        cnt += board[i + di][j + dj] & 1
                curr = board[i][j] & 1
                if (curr == 0 and cnt == 3) or (curr == 1 and (cnt == 2 or cnt == 3)):
                    board[i][j] += 2
        for i in range(m):
            for j in range(n):
                board[i][j] >>= 1
```
## Notes

記錄下一回合的生或死 最後bit shift

