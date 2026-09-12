---
tags:
  - dp
  - binarySearch
  - sorting
Difficulty Level: Hard
Rating: 2723
Need Review: true
Origin: 09/12 Daily
First: 2026-09-12
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-score-of-non-overlapping-intervals/description/?envType=daily-question&envId=2026-09-12)
先備知識：[[1235 - Maximum Profit in Job Scheduling]]
就是變強版的他，要注意到只能選4 個跟要多一個維度去儲存smaller index
關鍵一樣是：要選或不選現在這個 要選的話就是從left, k - 1 轉移過來 不選的話就是從i - 1, k 轉移過來


```python
class Solution:
    def maximumWeight(self, intervals: List[List[int]]) -> List[int]:
        a = [(r, l, w, i) for i, (l, r, w) in enumerate(intervals)]
        n = len(intervals)
        a.sort()
        dp = [[0 for _ in range(5)] for _ in range(n + 1)] # i, 0~4
        choice = [[[] for _ in range(5)] for _ in range(n + 1)]

        for i in range(n):
            l, r, w, index = a[i][1], a[i][0], a[i][2], a[i][3]
            left = bisect_left(a, (l,), hi=i)
            for k in range(1, 5):
                if dp[i][k] > dp[left][k - 1] + w:
                    dp[i + 1][k] = dp[i][k]
                    choice[i + 1][k] = choice[i][k]
                elif dp[i][k] == dp[left][k - 1] + w:
                    dp[i + 1][k] = dp[i][k]
                    choice[i + 1][k] = min(choice[i][k], sorted(choice[left][k - 1] + [index]))
                else:
                    dp[i + 1][k] = dp[left][k - 1] + w
                    choice[i + 1][k] = sorted(choice[left][k - 1] + [index])
        currMax = -inf
        ans = []
        for i in range(5):
            if dp[-1][i] > currMax:
                currMax = dp[-1][i]
                ans = choice[-1][i]
            elif dp[-1][i] == currMax:
                ans = min(ans, choice[-1][i])
        return ans
```

