---
tags:
  - stack
  - string
Difficulty Level: Easy
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/valid-parentheses/?envType=study-plan-v2&envId=top-interview-150)
記得key 是放右邊的括弧，因為我們是看到右括弧才去找左括弧夥伴

```python
class Solution:
    def isValid(self, s: str) -> bool:
        para = {')': '(', ']': '[', '}': '{'}
        st = []

        for c in s:
            if c in '([{':
                st.append(c)
            else:
                if not st:
                    return False
                left = st.pop()
                if left != para[c]:
                    return False
        
        return len(st) == 0
```

