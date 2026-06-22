---
tags:
  - hashTable
  - counting
  - string
Difficulty Level:
Rating:
Need Review: false
Origin:
First: 2026-06-22
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-number-of-balloons/?envType=daily-question&envId=2026-06-22)

```python
class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        ans = inf
        cnt = defaultdict(int)
        for c in text:
            if c in 'balon':
                cnt[c] += 1
        for c in 'ban':
            ans = min(cnt[c], ans)
        
        for c in 'lo':
            ans = min(cnt[c]//2, ans)
        
        return ans

```

