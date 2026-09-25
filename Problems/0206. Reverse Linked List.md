---
tags:
  - linkedList
  - recursion
Difficulty Level: Easy
Rating: 
Need Review: true
Origin: LC 206
First: April 16, 2025 7:58 PM
Watch Solution: false
---

# 206. Reverse Linked List

[Link](https://leetcode.com/problems/reverse-linked-list/description/)

**Topics**: Linked List, Recursion

## Notes

直接用一個pre, 然後每個箭頭轉過去就好 聰明！
步驟
1. 要先存head.next，因為會被蓋掉
2. 接著把head.next 指向一開始的pre 
3. 再來用pre = head
4. head = tmp （就是剛剛存的head.next 啦）

```python

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return head

        curr = None
        while head:
            tmp = head.next
            head.next = curr
            curr = head
            head = tmp
        return curr
```

