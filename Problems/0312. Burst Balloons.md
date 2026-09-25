---
tags:
  - array
  - dp
Difficulty Level: Hard
Rating: 
Need Review: true
Origin: LC 312
First: May 22, 2025 10:08 PM
Watch Solution: true
---

# 312. Burst Balloons

[Link](https://leetcode.com/problems/burst-balloons/description/)

**Topics**: Array, DP

## Notes

因為氣球被戳破之後會導致他的鄰居改變，所以如果我們一個一個去枚舉氣球被戳破的順序會很麻煩-> 飯過來思考，這個區間最後一個被戳的是誰？
可以用開區間，就是區間的兩端不會被戳

dp 轉移就變成`dp[i][j] = dp[i][k] + nums[i] * nums[k] * nums[j] + dp[k][j]`
為了方便處理我們可以在頭尾都加上一個1 當作邊界

以下：top down 寫法

``` python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        nums = [1] + nums + [1]
        n = len(nums)

        @cache
        def dfs(i, j):
            ans = 0
            for k in range(i + 1, j):
                ans = max(ans, dfs(i, k) + nums[i] * nums[k] * nums[j] + dfs(k, j))
            return ans
        return dfs(0, n - 1)

```

bottom up 寫法的話就是從長度為2 的開始往上推