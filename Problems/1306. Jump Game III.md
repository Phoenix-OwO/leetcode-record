---
tags:
  - bfs
  - dfs
  - array
Difficulty Level: Medium
Rating: 1396
Need Review: false
Origin: 05/17 Daily
First: 2026-05-17
Watch Solution: false
---
一眼看出可以bfs 然後一次過
沒什麼好說的：））
[link](https://leetcode.com/problems/jump-game-iii/?envType=daily-question&envId=2026-05-17)

```python
class Solution:
    def canReach(self, arr: List[int], start: int) -> bool:
        n = len(arr)
        visited = [False] * n
        visited[start] = True
        q = deque([start])
        while q:
            node = q.popleft()
            if arr[node] == 0:
                return True
            if node + arr[node] < n and not visited[node + arr[node]]:
                q.append(node + arr[node])
                visited[node + arr[node]] = True
            if node - arr[node] >= 0 and not visited[node - arr[node]]:
                q.append(node - arr[node])
                visited[node - arr[node]] = True
        return False
```

