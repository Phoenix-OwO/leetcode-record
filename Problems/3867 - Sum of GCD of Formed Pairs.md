---
tags:
  - math
  - twoPointers
Difficulty Level: Medium
Rating: 1406
Need Review: false
Origin: 07/16 Daily
First: 2026-07-16
Watch Solution: false
---
[link](https://leetcode.com/problems/sum-of-gcd-of-formed-pairs/?envType=daily-question&envId=2026-07-18)
題目都跟你說步驟怎麼做了。

```python
class Solution:
    def gcdSum(self, nums: list[int]) -> int:
        prefixGcd = []
        ans = 0
        mxi = -inf

        for num in nums:
            mxi = max(num, mxi)
            prefixGcd.append(gcd(mxi, num))
        
        prefixGcd.sort()
        n = len(nums)
        for i in range(n//2):
            ans += gcd(prefixGcd[i], prefixGcd[n - 1 - i])
        
        return ans

```

