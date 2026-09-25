---
tags:
  - linkedList
Difficulty Level: Easy
Rating: 
Need Review: false
Origin: LC 141
First: April 16, 2025 9:25 PM
Watch Solution: false
---

# 141. Linked List Cycle

[Link](https://leetcode.com/problems/linked-list-cycle/description/)

**Topics**: Linked List

有好幾種作法
1. 快慢指針fast 跟slow ptr 如果當他們相遇，代表有cycle ，因為fast 從後面趕上slow 了
2. 走過的改成一個不在範圍內的值（比如字符），如我下一個是這個直，代表先前走過了
3. 暴力地把所有看過的listnode 塞進一個set 裡面，如果遇到的已經在set 代表走過

```python


class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        if not head:
            return False
        slow = head

        while slow.next:
            if slow.val == 'a':
                return True
            slow.val = 'a'
            slow = slow.next
            
        return False

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        if not head:
            return False
        fast = head
        slow = head

        while slow.next and fast.next and fast.next.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                return True
        return False
```

