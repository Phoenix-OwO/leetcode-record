---
tags:
  - linkedList
  - math
  - recursion
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-06-15
Watch Solution: false
---
[link](https://leetcode.com/problems/add-two-numbers/?envType=study-plan-v2&envId=top-interview-150)

請務必記得dummy node 怎麼用！！
還有記得carry 要傳到下一位
最後如果還有carry 記得再補給他一個listnode


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = res = ListNode()
        curr = 0
        carry = 0

        while l1 and l2:
            carry, curr = divmod(l1.val + l2.val + carry, 10)
            dummy.next = ListNode(curr)
            dummy = dummy.next
            l1 = l1.next
            l2 = l2.next
        
        while l1:
            carry, curr = divmod(l1.val + carry, 10)
            dummy.next = ListNode(curr)
            dummy = dummy.next
            l1 = l1.next
        
        while l2:
            carry, curr = divmod(l2.val + carry, 10)
            dummy.next = ListNode(curr)
            dummy = dummy.next
            l2 = l2.next
        
        if carry > 0:
            dummy.next = ListNode(carry)

        return res.next

```

