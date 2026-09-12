---
tags:
Difficulty Level:
Rating:
Need Review: false
Origin: Biweekly 189
First: 2026-08-15
Watch Solution: false
---
[link](https://leetcode.com/problems/elevator-requests-ii/description/)
關鍵：看出是dp，不能greedy 做，因為早期的每一秒都很關鍵不能浪費！
下一步：想一下要怎麼轉移過來
今天先考慮只有一邊的狀況，假設五層分別是 2 3 5 7 8 ，我們要到8 的時候只要考慮從7 過來就好，因為從5 過來的話一定會經過7，再到8 
如果考慮兩邊的話，假設一樣是 2 3 5 7 8 ，start 是5，
```dp[i][j][right] = min(dp[i][j - 1][left] + costL, dp[i][j - 1][right] + costR``` 
```dp[i][j] = min(dp[i + 1][j][left] + costL, dp[i + 1][j][right] + costR```
所以他其實是一個區間dp 

最重要需要注意的事情是：因為start 有可能在裡面，也可能不在裡面，所以在算cost 的時候要注意rem （剩餘要被處罰的個數）
這邊使用的是check 這個數字來記錄
```python
class Solution:
    def elevatorRequests(self, n: int, start: int, requests: list[int]) -> int:
        cnt = len(requests)
        check = 0
        if start not in requests:
            check = 1
            requests.append(start)
        
        requests.sort()
        
        self.startPos = bisect_left(requests, start)

        @cache
        def dfs(i: int, j: int, right: bool) -> int:
            if not (i <= self.startPos <= j):
                return inf
            if i == j:
                return 0

            rem = cnt - (j - i - check)
            if right == True:
                ans = min(dfs(i, j - 1, True) + (requests[j] - requests[j - 1]) * rem, dfs(i, j - 1, False) + (requests[j] - requests[i]) * rem)
            else:
                ans = min(dfs(i + 1, j, False) + (requests[i + 1] - requests[i]) * rem, dfs(i + 1, j, True) + (requests[j] - requests[i]) * rem)
            return ans
        m = cnt + check
        ans = min(dfs(0, m - 1, True), dfs(0, m - 1, False))
        dfs.cache_clear()
        return ans
```

