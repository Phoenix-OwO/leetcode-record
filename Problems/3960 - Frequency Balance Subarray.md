---
tags:
  - enumeration
  - counting
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/frequency-balance-subarray/)
我看超級久

滿足題目的狀況有以下兩種

1. 裡面只有一種數字 
2. 裡面有不只一種數字，這些數字有剛好不多不少兩種出現頻率，而且其中一個是另一個的兩倍

因為範圍只有1500所以可以n 平方暴力過。

記錄每種數字出現幾次以及總共有幾種freq ，當滿足條件一或二時更新答案

```python
class Solution:
    def getLength(self, nums: List[int]) -> int:

        ans = 0
        n = len(nums)
        for i in range(n):
            freq = defaultdict(int)
            times = defaultdict(int)
            for j in range(i, n):
                if freq[nums[j]] != 0:
                    times[freq[nums[j]]] -= 1
                    if times[freq[nums[j]]] == 0:
                        del times[freq[nums[j]]]
                freq[nums[j]] += 1
                times[freq[nums[j]]] += 1
                
                if len(freq) == 1:
                    ans = max(ans, j - i + 1)
                elif len(times) == 2:
                    k1, k2 = times.keys()
                    if k1 == k2 * 2 or k1 * 2 == k2:
                        ans = max(ans, j - i + 1)
        return ans
                    
```

