---
tags:
  - bfs
  - string
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 433
First: August 16, 2025 3:54 PM
Watch Solution: false
---

# 433. Minimum Genetic Mutation

[Link](https://leetcode.com/problems/minimum-genetic-mutation/description/?envType=study-plan-v2&envId=top-interview-150)

**Topics**: BFS, String

## Notes

因為bank 很小 所以可以從end 推回去

```python
class Solution:
    def minMutation(self, startGene: str, endGene: str, bank: List[str]) -> int:
        q = deque([(0, startGene)])
        seen = set(startGene)
        bank = set(bank)

        def diff(g1, g2):
            cnt = 0
            for i in range(8):
                if g1[i] != g2[i]:
                    cnt += 1
            return cnt

        while q:
            d, gene = q.popleft()
            if gene == endGene:
                return d
            for g2 in bank:
                if g2 not in seen and diff(gene, g2) == 1:
                    q.append((d + 1, g2))
                    seen.add(g2)
        return -1
```