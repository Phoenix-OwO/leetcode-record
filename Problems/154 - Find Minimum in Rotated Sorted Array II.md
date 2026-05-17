---
tags:
  - binarySearch
Difficulty Level: Hard
Rating:
Need Review: true
Origin: 05/16 Daily
First: 2026-05-16
Watch Solution: false
---
[link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/description/?envType=daily-question&envId=2026-05-15)

看了[靈神的詳解](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array-ii/solutions/2131553/zhi-yao-ni-hui-153-jiu-neng-kan-dong-pyt-qqc6/?envType=daily-question&envId=2026-05-15)

左閉右開讚，覺得好像懂了。

這題的關鍵是：因為有相同的元素，如果```nums[mid]``` == ```nums[-1]``` 的話我們沒辦法分辨他是在左邊還是右邊那段，比如說 1 5 5 5 跟 6 5 5 5 5 ，```nums[mid]``` 都等於 ```nums[-1]``` 
這時候我們不能直接改左邊或者右邊，於是我們可以把尾巴那個丟掉（把right 往左邊移一格），
思考：如果尾巴的值不是min ，那我們刪掉了一個答案，如果左邊的值是min也沒關係，因為我們的mid 還是有壓到他所以不用擔心！

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l = -1
        r = len(nums) - 1

        while l + 1 < r:
            mid = (l + r) // 2
            if nums[mid] == nums[r]:
                r -= 1
            elif nums[mid] < nums[r]:
                r = mid
            else:
                l = mid
        return nums[r]

```

