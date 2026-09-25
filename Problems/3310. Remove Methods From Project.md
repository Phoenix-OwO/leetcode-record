---
tags:
  - bfs
  - dfs
Difficulty Level: Medium
Rating: 1710
Need Review: false
Origin: 08/05 Daily
First: 2026-08-05
Watch Solution: false
---
[link](https://leetcode.com/problems/remove-methods-from-project/description/?envType=daily-question&envId=2026-08-05)
看完題目之後不難做
總之就是兩次bfs 一次看所有可疑的點，另外一次看可疑的點有沒有被正常的點碰到。
更新：有想到一個剪枝，第二次bfs 只要針對所有正常節點看有沒有碰到sus 節點就好。

```python
class Solution:
    def remainingMethods(self, n: int, k: int, invocations: List[List[int]]) -> List[int]:
        adj = [[] for _ in range(n)]
        visited = [False] * n
        visited[k] = True
        sus = [False] * n
        sus[k] = True
        for u, v in invocations:
            adj[u].append(v)
        
        q = deque([k])
        while q:
            node = q.popleft()
            for nextNode in adj[node]:
                if not visited[nextNode]:
                    sus[nextNode] = True
                    visited[nextNode] = True
                    q.append(nextNode)
        
        visited = [False] * n
        q = deque()
        for i in range(n):
            if not sus[i]:
                for nextNode in adj[i]:
                    if sus[nextNode]:
                        return [i for i in range(n)]
        ans = []
        check = True
        for i in range(n):
            if sus[i] and visited[i]:
                return [i for i in range(n)]
        
        return [i for i in range(n) if not sus[i]]

        
```

