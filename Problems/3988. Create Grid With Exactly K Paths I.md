---
tags:
Difficulty Level: Hard
Rating:
Need Review: false
Origin:
First: 2026-07-12
Watch Solution: false
---
[link](https://leetcode.com/problems/create-grid-with-exactly-k-paths-i/description/)
我毫無頭緒，決定使出高中學排組的精神窮舉一下。
先特判沒有答案跟僅有一條的狀況。
```python
class Solution:
    def createGrid(self, m: int, n: int, k: int) -> list[str]:
        if (m == 1 or n == 1) and k > 1:
            return []
        if (m == 2 and n < k) or (n == 2 and m < k):
            return []
        if m == 1 and k == 1:
            return ['.' * n]
        if n == 1 and k == 1:
            return ['.' for _ in range(m)]
        
        if (n > 3 or (n == 3 and k < 4) or n == 2) and n >= k:
            ans = ['.' * n]
            ans.append('#' * (n - k) + '.' * k)
            for i in range(m - 2):
                ans.append('#' * (n - 1) + '.')
            return ans
        
        if n == 3 and k == 4:
            ans = ["..#","...","#.."]
            for i in range(m - 3):
                ans.append('#' * (n - 1) + '.')
            return ans
        if n == 2 and k > 2:
            ans = []
            for i in range(k):
                ans.append('.' * 2)
            for i in range(m - k):
                ans.append('#' + '.')
            return ans
```

