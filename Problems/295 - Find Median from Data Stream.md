---
tags:
  - priorityQueue
Difficulty Level: Hard
Rating:
Need Review: false
Origin: LC 295
First: May 30, 2025 5:04 PM
Watch Solution: false
---
對頂堆！
# 295. Find Median from Data Stream

[Link](https://leetcode.com/problems/find-median-from-data-stream/description/)

**Topics**: Heap (Priority Queue)

## Notes

用兩個heapq 來存 一個存大的 一個存小的 記得要維持小的那條長度≥長的那條 這樣才可以傳出正中間那個

class MedianFinder:
```python
    def __init__(self):
        self.larger = []
        self.smaller = []
    def addNum(self, num: int) -> None:
        heapq.heappush(self.smaller, -num)
        heapq.heappush(self.larger, -heapq.heappop(self.smaller))
        if len(self.larger) > len(self.smaller):
            heapq.heappush(self.smaller, -heapq.heappop(self.larger))

    def findMedian(self) -> float:
        if len(self.smaller) > len(self.larger):
            return -self.smaller[0]
        return (-self.smaller[0] + self.larger[0])/2
```
