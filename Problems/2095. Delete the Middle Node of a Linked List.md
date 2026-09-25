---
tags:
  - linkedList
  - twoPointers
Difficulty Level: Medium
Rating: 1324
Need Review: false
Origin: 06/15 Daily
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/?envType=daily-question&envId=2026-06-15)
用fast 跟slow 兩個指針，這樣就可以抓到正中間的人了

```python
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head.next
        if not fast:
            return slow.next
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        slow.next = slow.next.next

        return head
```

