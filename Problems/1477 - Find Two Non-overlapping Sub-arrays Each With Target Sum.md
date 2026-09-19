---
tags:
  - dp
  - binarySearch
  - hashTable
Difficulty Level: Medium
Rating: 1850
Need Review: false
Origin: 09/17 Daily
First: 2026-09-17
Watch Solution: false
---
[link](https://leetcode.com/problems/find-two-non-overlapping-sub-arrays-each-with-target-sum/?envType=daily-question&envId=2026-09-12) 
這題不難，就是dp 跟prefix sum 的題目，我們可以看每一個點的尾巴以他結尾的最短的subarray（透過除存prefix 的最右邊的位置 每一輪更新） 
接著如果這一個點有以他結尾的array，我們就可以從他的最左端點開始找前面有沒有，如果有的話就更新答案。
要注意：只有在有以這個點結尾的subarray 才可以更新答案、更新答案完之後記得用```dp[i - 1] ```更新```dp[i]``` 因為我們的dp array 存的是現在以前的最短subarray 所以如果是結尾在i - 1 也可以

```python
class Solution:
    def minSumOfLengths(self, arr: list[int], target: int) -> int:
        n = len(arr)
        dp = [inf] * n
        pre = {}
        pre[0] = -1
        ans = inf
        curr = 0

        for i, x in enumerate(arr):
            curr += x
            if curr - target in pre:
                dp[i] = i - pre[curr - target]
                if i - dp[i] >= 0 and dp[i - dp[i]] != inf:
                    ans = min(ans, dp[i] + dp[i - dp[i]])
            dp[i] = min(dp[i], dp[i - 1])
            pre[curr] = i
        return ans if ans != inf else -1
```

