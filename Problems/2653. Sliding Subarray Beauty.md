---
tags:
  - slidingWindow
  - heap
Difficulty Level: Medium
Rating: 1785
Need Review: false
Origin:
First: 2026-06-15
Watch Solution: false
---
[link](https://leetcode.com/problems/sliding-subarray-beauty/description/)

1785 分是暴力解，底下的是用對頂堆的非暴力解寫法。
一樣是lazy heap 的寫法，重要的要注意的點：出窗的時候要注意 ```nums[i - k]``` 有沒有 < 0，如果沒判斷的話right 的size 會炸掉（因為大於零的根本不在兩個array 裡面，可是卻會被判斷成在右邊的。

```python
class LazyHeap:
    def __init__(self):
        self.heap = []
        self.remove_cnt = defaultdict(int)  
        self.size = 0 

    def remove(self, x: int) -> None:
        self.remove_cnt[x] += 1 
        self.size -= 1

    def apply_remove(self) -> None:
        while self.heap and self.remove_cnt[self.heap[0]] > 0:
            self.remove_cnt[self.heap[0]] -= 1
            heappop(self.heap)

    def top(self) -> int:
        self.apply_remove()
        return self.heap[0]

    def pop(self) -> int:
        self.apply_remove()
        self.size -= 1
        return heappop(self.heap)

    def push(self, x: int) -> None:
        heappush(self.heap, x)
        self.size += 1

    def pushpop(self, x: int) -> int:
        self.apply_remove()
        return heappushpop(self.heap, x) 

class Solution:
    def getSubarrayBeauty(self, nums: List[int], k: int, x: int) -> List[int]:
        left = LazyHeap()
        right = LazyHeap()
        ans = []
        
        for i, num in enumerate(nums):
            # 1. in 
            if num < 0:
                if left.size < x:
                    left.push(-right.pushpop(num))
                else:
                    right.push(-left.pushpop(-num))
            # 2. out
            if i >= k and nums[i - k] < 0:
                if left.size > 0 and nums[i - k] <= -left.top():
                    left.remove(-nums[i - k])
                else:
                    right.remove(nums[i - k])
            while left.size < x and right.size > 0:
                left.push(-right.pop())

            if i >= k - 1:
                if left.size == x:
                    ans.append(-left.top())
                else:
                    ans.append(0)
        return ans
            

            



```

