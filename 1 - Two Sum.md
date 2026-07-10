---
tags:
  - array
  - hashTable
Difficulty Level:
Rating:
Need Review: false
Origin:
First: 2026-07-10
Watch Solution: false
---
[link](https://leetcode.com/problems/two-sum/description/)
對於每個數字，先檢查他的配對（另外一半）有沒有出現過了，如果有的話代表找到答案，如果沒有的話我們記錄這個數字出現的位置，之後繼續往下找

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = defaultdict(int)
        for i, x in enumerate(nums):
            if target - x in seen:
                return [i, seen[target - x]]
            seen[x] = i
```

