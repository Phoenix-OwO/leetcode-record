---
tags:
  - sorting
Difficulty Level: Medium
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/h-index/?envType=study-plan-v2&envId=top-interview-150)

關鍵是由大到小排，因為代表這個點以前的所有論文都有大於這個數值。
當這個點的citation數量 （x） <= index 代表說這個文獻以後都不符合，我們沒有找到更到的h 了，這時我們就結束。



```python
class Solution:
    def hIndex(self, citations: List[int]) -> int:

        citations.sort(reverse = True)
        for i, x in enumerate(citations):
            if x <= i:
                return i
        return len(citations)
```

