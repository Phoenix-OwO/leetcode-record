---
tags:
  - bfs
  - hashTable
  - bitmask
Difficulty Level: Medium
Rating: 2143
Need Review: false
Origin: 09/01 Daily
First: 2026-09-01
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-moves-to-clean-the-classroom/?envType=daily-question&envId=2026-09-01)
最原先的想法：seen 的set 記錄energy, r, c, key 但是呢 如果要記錄energy 的話會超時 TLE ！！！
這個時候就到了優化的出場時機了！此時可以想：充電是為了在更多的能量（更好的狀態下）去踩過這一格，讓我們可以走到更遠的地方（如果是更小的電量踩到這一格的話沒有用，因為他不會比先前走得更遠）
-> 改良seen 的array ，讓他不是當作visited 用，而是記錄走到這格的時候的最大電量，如果我們遇到了新的case 他踩到此刻時的能量比先前的狀態大，我們就把它加進dq 裡面，代表這個才有去跑bfs 的意義！


```python
class Solution:
    def minMoves(self, classroom: List[str], energy: int) -> int:
        direc = [(0,1), (0,-1), (1,0), (-1,0)]
        m, n = len(classroom), len(classroom[0])
        dq = deque()
        litters = defaultdict(int)
        l = 0
        for r in range(m):
            for c in range(n):
                if classroom[r][c] == 'S':
                    dq.append((0, energy, 0, r, c)) # moves energy key row column
                elif classroom[r][c] == 'L':
                    litters[(r,c)] = 1<<l
                    l += 1
        seen = [[[0 for _ in range(1<<l)]for _ in range(n)] for _ in range(m)]
        seen[dq[0][3]][dq[0][4]][0] = energy # r, c, k
        if l == 0:
            return 0
        
        target = (1<<l) - 1
        while dq:
            d, e, k, r, c = dq.popleft()
            if e == 0:
                continue
            for dr, dc in direc:
                if 0 <= dr + r < m and 0 <= dc + c < n and classroom[r + dr][c + dc] != 'X':
                    currK = k | litters[(r + dr, c + dc)]
                    if currK == target:
                        return d + 1
                    currE = energy if classroom[r + dr][c + dc] == 'R' else e - 1
                    if currE > seen[r + dr][c + dc][currK]:
                        seen[r + dr][c + dc][currK] = currE
                        dq.append((d + 1, currE, currK, r + dr, c + dc))

        return -1
                        

```

