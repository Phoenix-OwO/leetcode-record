---
tags:
  - dp
  - array
Difficulty Level: Medium
Rating: 1900
Need Review: false
Origin: Weekly 517
First: 2026-08-30
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-operations-to-form-subset-sum-i/description/)
剛看到的時候用dfs 寫到很躁
冷靜下來之後發現就是分組背包問題
每個東西可以被看成是它一直乘以2 或一直除以2 
這題限制說乘2 一定要在除2 的前面發生，但我們知道乘除乘除沒意義，只是徒增步數，所以我們可以把乘跟除分開想。
我有被一組測資3, 3, 3, 全部都一樣的卡住，所以決定預處理一下他們，這樣寫起來比較舒服．
時間複雜度是O(sum * n * log(num))

```python
class Solution:
    def minOperations(self, nums: list[int], sum: int) -> int:
        n = len(nums)
        dp = [inf for _ in range(sum + 1)]
        dp[0] = 0
        choice = defaultdict(list)
        for num in nums:
            if num in choice:
                continue
            cnt = 0
            curr = num
            c = []
            while curr <= sum:
                c.append((curr, cnt))
                curr *= 2
                cnt += 1
            cnt = 1
            curr = num //2
            while curr > 0:
                c.append((curr, cnt))
                curr //= 2
                cnt += 1            
            choice[num] = sorted(c)
        
        for num in nums:
            new_dp = dp.copy()
            for curr, cost in choice[num]:
                for i in range(sum - curr + 1):
                    new_dp[i + curr] = min(dp[i] + cost, new_dp[i + curr])
            dp = new_dp
        return dp[sum] if dp[sum] != inf else -1

```

