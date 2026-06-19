---
tags:
  - array
  - hashTable
  - slidingWindow
  - priorityQueue
Difficulty Level: Hard
Rating:
Need Review: true
Origin: LC 480
First: June 16, 2025 7:15 PM
Watch Solution: false
---

# 480. Sliding Window Median

[Link](https://leetcode.com/problems/sliding-window-median/description/)

**Topics**: Array, Hash Table, Heap (Priority Queue), Sliding Window

## Notes

用sorted list 作弊 = =
06/16/26 更新：出來混欠的總是要還的
用懶刪除堆+ 對頂堆
我只監控large 裡面的元素數量，用額外變數紀錄large 裡面刪掉的數量，長度 - delCnt 要維持一半的長度

偷了靈神的lazy heap 模板之後獲得了更厲害的啟發：
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
    def medianSlidingWindow(self, nums: List[int], k: int) -> List[float]:
        ans = []
        left = LazyHeap()
        right = LazyHeap()
        for i, x in enumerate(nums):
            # 1. in 
            if left.size == right.size:
                right.push(-left.pushpop(-x))
            else:
                left.push(-right.pushpop(x))
            # 2. out
            if i >= k:
                if nums[i - k] <= -left.top():
                    left.remove(-nums[i - k])
                else:
                    right.remove(nums[i - k])
            if left.size > right.size:
                right.push(-left.pop())
            if right.size > left.size + 1:
                left.push(-right.pop())
            # 3. Update
            if i >= k - 1:
                if k % 2 == 0:
                    ans.append((-left.top() + right.top())/2)
                else:
                    ans.append(right.top())
        return ans
```

```python
class Solution:
    def medianSlidingWindow(self, nums: List[int], k: int) -> List[float]:
        ans = []
        sH = []
        lH = []
        delCnt = 0
        h = ceil(k / 2)

        for i, x in enumerate(nums):
            heappush(sH, (-x, i))
            if i >= k:
                curr = nums[i - k]
                if (curr, i - k) >= lH[0]:
                    delCnt += 1
            while sH and sH[0][1] < (i - k + 1):
                heappop(sH)
            while lH and lH[0][1] < (i - k + 1):
                heappop(lH)
                delCnt -= 1
            if sH and lH and -sH[0][0] > lH[0][0]:
                lx, li = heappop(lH)
                sx, si = heappop(sH)
                heappush(lH, (-sx, si))
                heappush(sH, (-lx, li))
            while len(lH) - delCnt < h and sH:
                sx, si = heappop(sH)
                if si < (i - k + 1):
                    continue
                heappush(lH, (-sx, si))
            while sH and sH[0][1] < (i - k + 1):
                heappop(sH)
            while lH and lH[0][1] < (i - k + 1):
                heappop(lH)
                delCnt -= 1
            if i >= k - 1:
                if k % 2 == 0:
                    ans.append((lH[0][0] - sH[0][0]) / 2)
                else:
                    ans.append(lH[0][0])
        
        return ans
```



