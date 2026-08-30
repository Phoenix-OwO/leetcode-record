---
tags:
  - array
  - greedy
Difficulty Level: Medium
Rating: 1384
Need Review: false
Origin: 08/30 Daily
First: 2026-08-30
Watch Solution: false
---
[link](https://leetcode.com/problems/removing-minimum-and-maximum-from-array/?envType=daily-question&envId=2026-08-29)
找出min, max 這兩個數字出現在哪裡。
看誰比較左邊誰比較右邊
我們有三種刪法把這兩個元素踢掉：左邊刪（把比較右的以左都刪掉）、從右邊（把比較左的以右都刪掉）、或是從兩頭刪（小的以左、大的以右）
-> 找出最小的那個值

```python
class Solution:
    def minimumDeletions(self, nums: List[int]) -> int:
        minNum, minI = inf, -1
        maxNum, maxI = -inf, -1
        n = len(nums)

        for i, x in enumerate(nums):
            if x < minNum:
                minNum = x
                minI = i
            if x > maxNum:
                maxNum = x
                maxI = i
        minI, maxI = min(minI, maxI), max(minI, maxI)
        
        return min(maxI + 1, n - minI, minI + 1 + n - maxI)
```

