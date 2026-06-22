---
tags:
  - linkedList
  - twoPointers
Difficulty Level:
Rating:
Need Review: false
Origin:
First: 2026-06-22
Watch Solution: false
---
[link](https://leetcode.com/problems/partition-list/?envType=study-plan-v2&envId=top-interview-150)


```python
class Solution:
    def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
        dummy1 = res = ListNode()
        dummy2 = back = ListNode()

        while head:
            if head.val < x:
                dummy1.next = ListNode(head.val)
                dummy1 = dummy1.next
            else:
                dummy2.next = ListNode(head.val)
                dummy2 = dummy2.next
            head = head.next
        
        while dummy1.next:
            dummy1 = dummy1.next
        dummy1.next = back.next

        return res.next

```

