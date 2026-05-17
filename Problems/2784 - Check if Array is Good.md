---
tags:
  - hashTable
  - sorting
  - array
Difficulty Level: Easy
Rating: 1376
Need Review: false
Origin: 05/14 Daily
First: 2026-05-14
Watch Solution: false
---
[link](https://leetcode.com/problems/check-if-array-is-good/description/?envType=daily-question&envId=2026-05-14)
one pass 沒ㄌ

```python
class Solution:
    def isGood(self, nums: List[int]) -> bool:
        n = len(nums) - 1
        cnt = defaultdict(int)

        for i, x in enumerate(nums):
            cnt[x] += 1
            if x != n and cnt[x] > 1:
                return False 
            elif x == n and cnt[x] > 2:
                return False 
            elif x > n:
                return False
        return cnt[n] > 1
```

