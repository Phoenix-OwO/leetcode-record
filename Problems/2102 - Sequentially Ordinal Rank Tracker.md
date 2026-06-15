---
tags:
Difficulty Level: Hard
Rating: 2158
Need Review: true
Origin:
First: 2026-06-15
Watch Solution: true
---

[link](https://leetcode.com/problems/sequentially-ordinal-rank-tracker/description/)

怎麼說呢？原本想說對頂堆，維護larger 跟smaller 兩個，可是在smaller 要 -score, name 在右邊要score, -name  字串又不能直接負，所以我們只好用新東西：sorted list。
把它充當平衡樹用
看[靈神詳解](https://leetcode.cn/problems/sequentially-ordinal-rank-tracker/solutions/1152448/qiao-miao-li-yong-cha-xun-de-te-shu-xing-7eyg/)

平衡樹就是AVL tree 之前有講過但一直沒有學

```python
class SORTracker:
    def __init__(self):
        self.d = SortedList()
        self.i = 0

    def add(self, name: str, score: int) -> None:
        self.d.add((-score, name))

    def get(self) -> str:
        self.i += 1
        return self.d[self.i - 1][1]
```

