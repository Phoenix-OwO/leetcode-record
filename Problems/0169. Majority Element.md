---
tags:
  - divideAndConquer
  - sorting
  - hashTable
  - array
  - counting
Difficulty Level: Easy
Rating:
Need Review: false
Origin:
First: 2026-05-17
Watch Solution: false
---
Boyer–_Moore_ majority vote algorithm

[link](https://leetcode.com/problems/majority-element/description/?envType=study-plan-v2&envId=top-interview-150)

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        cnt, maj = 0, 0
        for num in nums:
            if num == maj:
                cnt += 1
            elif cnt > 0:
                cnt -= 1
            else:
                maj = num
                cnt = 1
        return maj
```

