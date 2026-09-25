---
tags:
  - bfs
  - matrix
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 200
First: April 12, 2025 11:37 AM
Watch Solution: false
---

# 200. Number of Islands

**Topics**: BFS, Matrix
看到新的島的時候發現新大陸，所以 cnt + 1
## Notes

BFS, DFS經典題
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        direc = [(0, -1), (0, 1), (1, 0), (-1, 0)]
        m = len(grid)
        n = len(grid[0])
        seen = [[False for _ in range(n)] for _ in range(m)]

        def bfs(i, j) -> None:
            q = deque([(i, j)])
            while q :
                currI, currJ = q.popleft()
                for di, dj in direc:
                    if 0 <= currI + di < m and 0 <= currJ + dj < n and grid[currI + di][currJ + dj] == '1' and not seen[currI + di][currJ + dj]:
                        q.append((currI + di, currJ + dj))
                        seen[currI + di][currJ + dj] = True
        
        cnt = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == "1" and not seen[i][j]:
                    cnt += 1
                    bfs(i, j)

        return cnt

```

Follow up （可能是一個訂閱題）: 如果有多給你一塊陸地（填海造陸），希望你可以找到最大的陸地的話怎麼辦？

我的想法：Union Find 去看每一個```grid[i][j] ``` 屬於哪一個union，然後填海的時候從海出發看能不能串


