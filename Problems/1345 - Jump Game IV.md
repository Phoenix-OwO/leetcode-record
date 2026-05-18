---
tags:
Difficulty Level: Hard
Rating: 1809
Need Review: false
Origin: 05/18 Daily
First: 2026-05-18
Watch Solution: false
---
[link](https://leetcode.com/problems/jump-game-iv/description/?envType=daily-question&envId=2026-05-18)

儲存所有同樣數字的index ，可以用defaultdict 存，踩完即可刪掉以免浪費時間
總之就是簡單快樂的bfs

```python
class Solution:
    def minJumps(self, arr: List[int]) -> int:
        occur = defaultdict(list)
        n = len(arr)
        q = deque([(0, 0)]) # node(index), d
        visited = [False] * n
        visited[0] = True
        
        for i, x in enumerate(arr):
            occur[x].append(i)
        
        while q :
            node, d = q.popleft()
            if node == n - 1:
                return d
            if node + 1 <= n - 1 and not visited[node + 1]:
                q.append((node + 1, d + 1))
                visited[node + 1] = True
            if node - 1 >= 0 and not visited[node - 1]:
                q.append((node - 1, d + 1))
                visited[node - 1] = True

            for adj in occur[arr[node]]:
                if not visited[adj]:
                    q.append((adj, d + 1))
                    visited[adj] = True
            occur[arr[node]] = []
    

```

