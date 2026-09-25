---
tags:
  - array
  - math
  - stack
Difficulty Level: Medium
Rating:
Need Review: true
Origin: LC 150
First: March 27, 2025 12:54 PM
Watch Solution: false
---

# 150. Evaluate Reverse Polish Notation

[Link](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/?envType=study-plan-v2&envId=top-interview-150)

``` python 
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        st = []

        for s in tokens:
            if s in '+-*/':
                a, b = st.pop(), st.pop() # -1, -2
                if s == '+':
                    st.append(b + a)
                if s == '-':
                    st.append(b - a)
                if s == '*':
                    st.append(b * a)
                if s == '/':
                    st.append(int(b/a))
            else:
                st.append(int(s))
        
        return st[0]
```

## Notes

經典stack 題 要小心除法 如果其中有個是負數的case (題目要求趨近0)

可以用int(b/a)的方式 ！重要
