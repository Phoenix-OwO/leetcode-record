---
tags:
  - linkedList
  - twoPointers
Difficulty Level: Medium
Rating:
Need Review: false
Origin: 06/14 Daily
First: 2026-06-14
Watch Solution: false
---
[link]()

```python
class Solution:
    def pairSum(self, head: Optional[ListNode]) -> int:
        twin = []
        num = 0
        fast = head
        slow = head
        while fast and fast.next:
            twin.append(slow.val)
            num += 1
            slow = slow.next
            fast = fast.next.next
        ans = 0
        n = 0
        while slow:
            ans = max(ans, twin[num-n-1]+slow.val)
            num -=1
            slow = slow.next
        return ans
```

