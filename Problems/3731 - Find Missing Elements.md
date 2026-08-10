---
tags:
  - array
  - hashTable
  - sorting
Difficulty Level: Easy
Rating: 1217
Need Review: false
Origin: 08/04 Daily
First: 2026-08-02
Watch Solution: false
---
[link](https://leetcode.com/problems/find-missing-elements/description/?envType=daily-question&envId=2026-08-05) 
照做

```python
class Solution:
    def findMissingElements(self, nums: List[int]) -> List[int]:
        l = min(nums)
        r = max(nums)
        s = set(nums)
        ans = []
        for i in range(l, r + 1):
            if i not in s:
                ans.append(i)
        return ans
```

