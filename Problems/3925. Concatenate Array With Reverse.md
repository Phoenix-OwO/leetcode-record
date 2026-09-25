---
tags:
Difficulty Level: Easy
Rating: 1200
Need Review: false
Origin: Weekly 501
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/concatenate-array-with-reverse/)
就這樣，沒什麼好說的

```python
class Solution:
    def concatWithReverse(self, nums: list[int]) -> list[int]:
        return nums + nums[::-1]
```

