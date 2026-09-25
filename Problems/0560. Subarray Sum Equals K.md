---
tags:
  - array
  - hashTable
  - prefixSum
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-07-10
Watch Solution: false
---
[link](https://leetcode.com/problems/subarray-sum-equals-k/description/)
因為要算幾個，不是最長或是最短，所以挑prefix sum 寫法
記錄前面出現過的和為多少的數字出現幾次，大概是這樣
當前總和比k 多多少代表我們應該減掉多少，所以就看前面有幾個subarray 等於這個數字，

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        pre = defaultdict(int)
        curr = 0
        pre[0] = 1
        ans = 0
        for i, x in enumerate(nums):
            curr += x
            ans += pre[curr - k]
            pre[curr] += 1        
        return ans
```

