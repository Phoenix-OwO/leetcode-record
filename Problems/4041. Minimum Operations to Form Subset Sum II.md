---
tags:
  - dp
  - array
Difficulty Level: Hard
Rating: 2100
Need Review: true
Origin: Weekly 517
First: 2026-08-30
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-operations-to-form-subset-sum-ii/description/)
前面那題的進階題
關鍵是要看出每個數字可以弄出哪些組合，比如11100 可以變成11或1 再左移，我們可以對於每一個都先左移，再來計算右移的部分，分別用a 跟b 記錄左右移的次數。
如果我們抵達這個數字花費的次數（a+b）比先前的多，代表不用再繼續往左移了，因為前面遇過了（這樣可以避免重複）
剩下的就跟前面那題一樣是分組背包問題，結束。

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
            tmp = num
            curr = num
            c = defaultdict(int)

            a = 0
            while num > 0:
                curr = num
                b = 0
                while curr <= sum:
                    if curr not in c or c[curr] > a + b:
                        c[curr] = a + b
                        curr *= 2
                        b += 1
                    else:
                        break
                num //= 2
                a += 1
            
            choice[tmp] = sorted((k, v) for k, v in c.items())
        for num in nums:
            new_dp = dp.copy()
            for curr, cost in choice[num]:
                for i in range(sum - curr + 1):
                    new_dp[i + curr] = min(dp[i] + cost, new_dp[i + curr])
            dp = new_dp
        return dp[sum] if dp[sum] != inf else -1

```

