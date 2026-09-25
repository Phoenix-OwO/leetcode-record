---
tags:
Difficulty Level: Easy
Rating:
Need Review: false
Origin: Biweekly 189
First: 2026-08-15
Watch Solution: false
---
[link](https://leetcode.com/problems/elevator-requests-i/description/)
照做而已

```python
class Solution:
    def elevatorRequests(self, n: int, requests: list[int]) -> int:
        ans = 0
        ans += abs(requests[0] - 0)
        n = len(requests)
        for i in range(1, n):
            ans += abs(requests[i] - requests[i - 1])
        return ans
```

