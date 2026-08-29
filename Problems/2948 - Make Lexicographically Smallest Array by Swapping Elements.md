---
tags:
Difficulty Level: Medium
Rating: 2047
Need Review: false
Origin: LC 2948
First: October 17, 2025 4:05 PM
Watch Solution: false
---

# 2948. Make Lexicographically Smallest Array by Swapping Elements

## Notes

我只想到union find，靈神詳解有分組討論，就是把index 跟num 一起放進去sort ，如果他們的絕對值都有≤ limit ，就代表他們可以分成一組，分完之後把他們按照順序填進去。

0829 更新：
分組討論讚的，先按照大小排好，就可以輕鬆抓出這組的頭尾，然後按照index 把排好的順序一一放入對應的格子，就順利地完成囉！

```python
class Solution:
    def lexicographicallySmallestArray(self, nums: List[int], limit: int) -> List[int]:
        arr = [(x, i) for i, x in enumerate(nums)]
        arr.sort()
        n = len(nums)
        i = 0
        while i < n:
            start = i
            i += 1
            while i < n and (arr[i][0] - arr[i - 1][0]) <= limit:
                i += 1
            indx = sorted(list(arr[curr][1] for curr in range(start, i)))
            for j in range(start, i):
                nums[indx[j - start]] = arr[j][0]
        return nums
```