---
tags:
  - linkedList
  - recursion
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-06-15
Watch Solution: false
---
[link](https://leetcode.com/problems/merge-two-sorted-lists/?envType=study-plan-v2&envId=top-interview-150)

如果list1 跟list2 都有就比大小，如果沒有的話，就把剩下的接上去

```python

class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = res = ListNode()

        while list1 and list2:
            if list1.val <= list2.val:
                dummy.next = ListNode(list1.val)
                dummy = dummy.next
                list1 = list1.next
            else:
                dummy.next = ListNode(list2.val)
                dummy = dummy.next
                list2 = list2.next
        if list1:
            dummy.next = list1
        if list2:
            dummy.next = list2
        
        return res.next
```

