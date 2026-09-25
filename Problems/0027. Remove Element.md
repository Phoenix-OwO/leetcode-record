---
tags:
  - twoPointers
  - array
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-18
Watch Solution: false
---
[link](https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150)

用left 跟 right pointer 去記錄現在換到的位置，因為k 以後的不用看，所以我們可以把不需要的元素由後往前的堆在不會被看到的地方。
今天的問題：用left 的話可能會卡到```nums``` 的長度是 0 的狀況

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        n = len(nums)
        r = n - 1
        l = 0
        cnt = 0
        while l <= r:
            if nums[l] == val:
                nums[l], nums[r] = nums[r], nums[l]
                r -= 1
            else:
                cnt += 1
                l += 1
        return cnt
```

