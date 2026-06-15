---
tags:
  - segmentTree
  - binarySearch
Difficulty Level: Hard
Rating:
Need Review: true
Origin: practice sweep line
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/my-calendar-iii/description/)

就是差分，不過他有[動態開點線段樹](https://leetcode.cn/problems/my-calendar-iii/solutions/1537825/by-ac_oier-ioyt/) 可以用= =


```python
class MyCalendarThree:
    def __init__(self):
        self.seen = defaultdict(int)
        
    def book(self, startTime: int, endTime: int) -> int:
        curr = 0
        ans = 0
        self.seen[startTime] += 1
        self.seen[endTime] -= 1
        
        for k, v in sorted(self.seen.items()):
            curr += v
            ans = max(curr, ans)

        return ans

```

