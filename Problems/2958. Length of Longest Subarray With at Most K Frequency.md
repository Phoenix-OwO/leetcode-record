---
tags:
  - array
  - hashTable
  - slidingWindow
Difficulty Level: Medium
Rating: 1535
Need Review: false
Origin: LC 2958
First: April 23, 2025 8:05 PM
Watch Solution: false
---

# 2958. Length of Longest Subarray With at Most K Frequency

[Link](https://leetcode.com/problems/length-of-longest-subarray-with-at-most-k-frequency/description/)

**Topics**: Array, Hash Table, Sliding Window

```python
class Solution:
    def maxSubarrayLength(self, nums: List[int], k: int) -> int:
        cnt = defaultdict(int)
        l = 0
        ans = 0
        for i, num in enumerate(nums):
            cnt[num] += 1
            while cnt[num] > k:
                cnt[nums[l]] -= 1
                l += 1
            if cnt[num] <= k:
                ans = max(ans, i - l + 1)
        return ans
```