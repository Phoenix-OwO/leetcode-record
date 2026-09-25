---
tags:
  - bfs
  - math
Difficulty Level: Medium
Rating: 2137
Need Review: true
Origin: LC 3629
First: July 27, 2025 8:28 PM
Watch Solution: false
---

# 3629. Minimum Jumps to Reach End via Prime Teleportation

[Link](https://leetcode.com/problems/minimum-jumps-to-reach-end-via-prime-teleportation/)

**Topics**: BFS, Math

## Notes

就是BFS。

關鍵是預處理好每個數的質因數、看完一個質數之後把它從dict 刪掉（預防後面重複看）、往前往後都可以走(i+1, i-1)

不知道為什麼想到 [[3715 - Sum of Perfect Square Ancestors]] 都是質數的題目，把他們連起來好了。

```python 
MX = 1_000_001
primeF = [[] for _ in range(MX)]
for i in range(2, MX):
    if not primeF[i]:
        for j in range(i, MX, i): 
            primeF[j].append(i)


class Solution:
    def minJumps(self, nums: List[int]) -> int:

        groups = defaultdict(list)
        for i, x in enumerate(nums):
            for p in primeF[x]:
                groups[p].append(i)
        
        n = len(nums)
        ans = 0
        visited = [True] + [False]*(n-1)

        q = deque([(0, 0)])
        while q:
            node, d = q.popleft()
            if node == n-1:
                return d
            for nextN in groups[nums[node]]:
                if not visited[nextN]:
                    q.append((nextN, d+1))
                    visited[nextN] = True
            if not visited[node+1]:
                q.append((node+1, d+1))
                visited[node+1] = True
            if node > 0 and not visited[node-1]:
                q.append((node-1, d+1))
                visited[node-1] = True
            groups[nums[node]].clear()


        return d
```
