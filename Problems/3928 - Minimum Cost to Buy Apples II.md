---
tags:
Difficulty Level: Hard
Rating: 2100
Need Review: false
Origin:
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-cost-to-buy-apples-ii/description/)
簡單的dijkstra 有剪枝方法，就是如果沒有< ```prices[i]``` 就不要更新了，浪費時間

```python
class Solution:
    def minCost(self, n: int, prices: List[int], roads: List[List[int]]) -> List[int]:
        ans = [0] * n
        path = [[] for _ in range(n)]
        for u, v, c, t in roads:
            path[u].append((v, c, t))
            path[v].append((u, c, t))
        for i in range(n):
            cost = [[inf for _ in range(2)] for _ in range(n)]
            cost[i][0] = 0
            cost[i][1] = prices[i]
            pq = [(0, i, 0)] # d, node, apple
            while pq:
                d, node, apple = heappop(pq)
                if d > cost[node][apple]:
                    continue
                if d + prices[node] < cost[node][1]:
                    cost[node][1] = d + prices[node]
                    heappush(pq, (d + prices[node], node, 1))
                if apple == 0:
                    for u, c, t in path[node]:
                        if d + c < cost[u][0]:
                            cost[u][0] = d + c
                            heappush(pq, (d + c, u, 0))
                else:
                    for u, c, t in path[node]:
                        if d + c * t < cost[u][1]:
                            cost[u][1] = d + c * t
                            heappush(pq, (d + c * t, u, 1))                    
            ans[i] = cost[i][1]
        return ans
        
```

剪枝之後
```python
class Solution:
    def minCost(self, n: int, prices: List[int], roads: List[List[int]]) -> List[int]:
        ans = [p for p in prices]
        maxP = max(prices)
        path = [[] for _ in range(n)]
        for u, v, c, t in roads:
            if c <= maxP:
                path[u].append((v, c, t))
                path[v].append((u, c, t))
        for i in range(n):
            cost = [[inf for _ in range(2)] for _ in range(n)]
            cost[i][0] = 0
            cost[i][1] = prices[i]
            pq = [(0, i, 0)] # d, node, apple
            while pq:
                d, node, apple = heappop(pq)
                if d > cost[node][apple]:
                    continue
                if d + prices[node] < ans[i] and d + prices[node] < cost[node][1]:
                    cost[node][1] = d + prices[node]
                    heappush(pq, (d + prices[node], node, 1))
                if apple == 0:
                    for u, c, t in path[node]:
                        if d + c < cost[u][0]:
                            cost[u][0] = d + c
                            heappush(pq, (d + c, u, 0))
                else:
                    for u, c, t in path[node]:
                        if d + c * t < ans[i] and d + c * t < cost[u][1]:
                            cost[u][1] = d + c * t
                            heappush(pq, (d + c * t, u, 1))                    
            ans[i] = cost[i][1]
        return ans
        
```