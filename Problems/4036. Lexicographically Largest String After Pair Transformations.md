---
tags:
Difficulty Level:
Rating:
Need Review: false
Origin: Biweekly 190
First: 2026-08-29
Watch Solution: false
---
[link](https://leetcode.com/problems/lexicographically-largest-string-after-pair-transformations/submissions/2128575033/)
greedy 然後二進位
先看他除以2 ** 25 是多少，這代表前面有幾個z ，剩下的就是從y 往下，就是看他跟2 ** 25 ...24 and起來是不是0，如果不是0 代表有一個這個字母，是0代表沒有
```python
class Solution:
    def largestString(self, nums: list[int]) -> list[str]:
        ans = []
        for num in nums:
            curr = []
            for i in range(25):
                if num & (1 << i) != 0:
                    curr.append(chr(ord('a') + i))
            ans.append('z' * (num//(1<<25)) + ''.join(curr[::-1]))
        return ans
```

