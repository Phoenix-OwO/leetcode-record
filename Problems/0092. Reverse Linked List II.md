---
tags:
  - linkedList
Difficulty Level: Medium
Rating: 
Need Review: false
Origin: LC 92
First: April 16, 2025 8:26 PM
Watch Solution: false
---

# 92. Reverse Linked List II

[Link](https://leetcode.com/problems/reverse-linked-list-ii/description/)

**Topics**: Linked List

## Notes

去數每一個node 現在是第幾個，如果= left 的話就先break ，去跑reverse 的那個方法，reverse 完之後我們就把剩下的接在後面，完成！


```python

class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        dummy = res = ListNode()
        cnt = 0
        curr = None

        while head:
            cnt += 1
            if left == cnt:
                break
            dummy.next = ListNode(head.val)
            dummy = dummy.next
            head = head.next
        
        while head:
            tmp = head.next
            head.next = curr
            curr = head
            head = tmp
            cnt += 1
            if cnt > right:
                dummy.next = curr
                break
        
        while dummy.next:
            dummy = dummy.next
        if head:
            dummy.next = head
        
        return res.next

        
```


