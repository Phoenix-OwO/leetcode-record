---
tags:
  - sorting
  - array
Difficulty Level: Medium
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-22
Watch Solution: false
---
[link](https://leetcode.com/problems/merge-intervals/description/?envType=study-plan-v2&envId=top-interview-150)

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        ans = []
        intervals.sort()
        s, e = intervals[0]

        for i in range(1, len(intervals)):
            if intervals[i][0] <= e:
                e = max(e, intervals[i][1])
            else:
                ans.append([s, e])
                s, e = intervals[i][0], intervals[i][1]
        
        ans.append([s, e])
        return ans
```

由開始時間 從小到大sort，如果遇到start <= end 代表 他們有重疊到