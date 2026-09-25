---
tags:
  - queue
  - slidingWindow
  - heap
  - monotonicQueue
Difficulty Level: Medium
Rating: 1672
Need Review: false
Origin:
First: 2026-07-28
Watch Solution: false
---
[link](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/)

看的第一眼以為是lazy heap + sliding window 
多看幾眼發現其實就是sliding window maximum那題，這個需要多一個monotonic queue，用來maintain 最小值，difference 就是最大值跟最小值（兩個q 的最前端）的差值
大概是這樣
但還沒研究為為什麼beats 這麼少人= =

```python
class Solution:
    def longestSubarray(self, nums: List[int], limit: int) -> int:
        l = 0
        ans = 0
        minQ = deque() 
        maxQ = deque() 
        for i, x in enumerate(nums):
            while minQ and x <= nums[minQ[-1]]:
                minQ.pop()
            while maxQ and x >= nums[maxQ[-1]]:
                maxQ.pop()
            minQ.append(i)
            maxQ.append(i)
            while minQ and maxQ and nums[maxQ[0]] - nums[minQ[0]]> limit:
                if minQ[0] == l:
                    minQ.popleft()
                if maxQ[0] == l:
                    maxQ.popleft()
                l += 1
            ans = max(ans, i - l + 1)
        return ans
            
```

