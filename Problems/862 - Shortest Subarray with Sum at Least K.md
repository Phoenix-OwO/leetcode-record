---
tags:
  - prefixSum
  - queue
Difficulty Level: Hard
Rating: 2306
Need Review: true
Origin: LC 862
First: May 23, 2025 9:55 PM
Watch Solution: true
---

# 862. Shortest Subarray with Sum at Least K

**Topics**: Prefix Sum, Queue

## Notes

乍看之下很sliding window 但其實不行 ，要用monotonic 的deque跟prefix sum 去減
```python
class Solution:
    def shortestSubarray(self, nums: List[int], k: int) -> int:

        n = len(nums)
        minL = inf
        prefix = [0]*(n+1)

        for i in range(n):
            prefix[i + 1] = prefix[i] + nums[i]
        
        q = deque()
        for i in range(n+1):
            while q and prefix[i] - prefix[q[0]] >= k:
                minL = min(minL, i - q.popleft())
            while q and prefix[i] <= prefix[q[-1]]:
                q.pop()
            q.append(i)
        return minL if minL != inf else -1
```