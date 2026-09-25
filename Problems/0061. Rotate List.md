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
[link](https://leetcode.com/problems/rotate-list/?envType=study-plan-v2&envId=top-interview-150)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def rotateRight(self, head, k):
        if not head:
            return head
        if k == 0:
            return head
        cnt = 0
        tmp = head
        while tmp:
            cnt += 1
            tmp = tmp.next
        
        k = k % cnt
        k = cnt - k
        dummy1 = curr = ListNode() # 前半
        dummy2 = res = ListNode() # 後半

        cnt = 0
        while head:
            cnt += 1
            if cnt > k:
                break
            dummy1.next = ListNode(head.val)
            dummy1 = dummy1.next
            head = head.next
        
        while head:
            dummy2.next = ListNode(head.val)
            dummy2 = dummy2.next
            head = head.next
        while dummy2.next:
            dummy2 = dummy2.next
        

        dummy2.next = curr.next

        return res.next

```

