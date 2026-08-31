---
tags:
  - linkedList
Difficulty Level: Medium
Rating: 1310
Need Review: false
Origin: 08/31 Daily
First: 2026-08-31
Watch Solution: false
---
[link](https://leetcode.com/problems/find-the-minimum-and-maximum-number-of-nodes-between-critical-points/description/?envType=daily-question&envId=2026-08-31)
記得前一個跟前前一個就好 
這樣就可以算前一個是不是critical
submit 之後發現cnt 不用減一 因為他們是相對的
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def nodesBetweenCriticalPoints(self, head: Optional[ListNode]) -> List[int]:
        p, pp = -1, -1
        firstCri = -1
        prevCri = -1
        minDis = inf
        maxDis = -inf
        cnt = 0
        while head:
            cnt += 1
            if p != -1 and pp != -1:
                if (p > pp and p > head.val) or (p < pp and p < head.val):
                    if firstCri != -1:
                        maxDis = max(maxDis, cnt - 1 - firstCri)
                    else:
                        firstCri = cnt - 1
                    if prevCri != -1:
                        minDis = min(minDis, cnt - 1 - prevCri)
                    
                    prevCri = cnt - 1
            pp, p = p, head.val
            head = head.next
        return [minDis, maxDis] if minDis != inf else [-1, -1]
```

