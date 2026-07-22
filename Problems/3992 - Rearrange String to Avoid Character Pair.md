---
tags:
Difficulty Level: Easy
Rating:
Need Review: false
Origin: Biweekly 187
First: 2026-07-18
Watch Solution: false
---
[link](https://leetcode.com/problems/rearrange-string-to-avoid-character-pair/)
先把y 抓出來 擺在最前面，剩下就可以按照字母順序隨便排，讚

```python
class Solution:
    def rearrangeString(self, s: str, x: str, y: str) -> str:
        cnt = Counter(s)
        ans = []
        if cnt[y] > 0:
            for _ in range(cnt[y]):
                ans.append(y)
        for c in cnt.keys():
            if c == y:
                continue
            for _ in range(cnt[c]):
                ans.append(c)

        return ''.join(ans)
```

