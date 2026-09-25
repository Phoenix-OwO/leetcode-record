---
tags:
  - array
  - matrix
  - simulation
Difficulty Level: Medium
Rating: 1766
Need Review: false
Origin: 05/09 Daily
First:
Watch Solution: false
---
[link](https://leetcode.com/problems/cyclically-rotating-a-grid/description/?envType=daily-question&envId=2026-05-09)

邪惡轉轉題，我直接用一個array 存整條，感覺可以in place 的做，但體感上會麻煩很多

```python
class Solution:
    def rotateGrid(self, grid: List[List[int]], k: int) -> List[List[int]]:
        m = len(grid)
        n = len(grid[0])
        for off in range(min(m, n)//2):
            arr = []
            for j in range(off, n - off):
                arr.append(grid[off][j])
            for i in range(off + 1, m - off - 1):
                arr.append(grid[i][n - off - 1])
            for j in range(n - 1 - off, off - 1, -1):
                arr.append(grid[m - 1 - off][j])
            for i in range(m - 2 - off, off, -1):
                arr.append(grid[i][off])
            cnt = 0
            l = len(arr)
            for j in range(off, n - off):
                grid[off][j] = arr[(cnt + k) % l]
                cnt += 1
            for i in range(off + 1, m - off - 1):
                grid[i][n - off - 1] = arr[(cnt + k) % l]
                cnt += 1
            for j in range(n - 1 - off, off - 1, -1):
                grid[m - 1 - off][j] = arr[(cnt + k) % l]
                cnt += 1
            for i in range(m - 2 - off, off, -1):
                grid[i][off] = arr[(cnt + k) % l]
                cnt += 1
        return grid
```

