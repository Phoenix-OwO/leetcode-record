---
tags:
Difficulty Level: Hard
Rating: 2155
Need Review: true
Origin: BiWeekly 181
First:
Watch Solution: true
---
方法一：
（那種二分找第k 大的題型）
[[1201 - Ugly Number III]]
[[786 - K-th Smallest Prime Fraction]]

```python
class Solution:
    def kthRemainingInteger(self, nums: list[int], queries: list[list[int]]) -> list[int]:
        even = [x for i, x in enumerate(nums) if x % 2 == 0]
        n = len(queries)
        ans = [0] * n
        def check(x: int) -> bool:
            xPos = bisect_right(even, x)
            right = bisect_right(even, nums[r])
            left = bisect_right(even, nums[l] - 1)
            if xPos < left:
                return x//2 >= k
            return x//2 - (min(right, xPos) - left) >= k
        for i, (l, r, k) in enumerate(queries):
            low = 0
            high = 2 * 10 ** 9 + 10 ** 6
            
            while low <= high:
                mid = (low + high) // 2
                if check(mid):
                    high = mid - 1
                else:
                    low = mid + 1
            ans[i] = low
        return ans
```


方法二前置：
[[1539 - Kth Missing Positive Number]]

