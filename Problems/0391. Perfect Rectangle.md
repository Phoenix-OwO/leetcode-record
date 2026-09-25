---
tags:
  - array
  - hashTable
  - geometry
  - sweepLine
Difficulty Level: Hard
Rating:
Need Review: false
Origin: practice sweep line
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/perfect-rectangle/)

好醜。
關鍵：所有非左右的都會一組一組配對，最左邊跟最右邊的話，一個y 座標一次只會有一條。
說到底還是看了[這個解答](https://leetcode.cn/problems/perfect-rectangle/solutions/1104133/gong-shui-san-xie-chang-gui-sao-miao-xia-p4q4/)

```python
class Solution:
    def isRectangleCover(self, rectangles: List[List[int]]) -> bool:
        seen = defaultdict(int)
        n = len(rectangles)
        ll = defaultdict(int)
        rr = defaultdict(int)

        left = min(rectangles[i][0] for i in range(n))
        right = max(rectangles[i][2] for i in range(n))

        for x, y, a, b in rectangles:
            if x != left:
                seen[(x, y, b)] += 1 
            else:
                ll[y] += 1
                ll[b] -= 1
            if a != right:
                seen[(a, y, b)] -= 1
            else:
                rr[y] += 1
                rr[b] -= 1

        def check(occur) -> bool:
            curr = 0
            for k, v in sorted(occur.items()):
                curr += v
                if curr != 0:
                    return False
            return True
        def checkB(occur) -> bool:
            curr = 0
            for k, v in sorted(occur.items()):
                curr += v
                if curr > 1:
                    return False
            return True
        prevX = -inf
        curr = defaultdict(int)
        for (x, y, l), cnt in sorted(seen.items()):
            if x != prevX:
                if not check(curr):
                    return False
                prevX = x
                curr = defaultdict(int)
            curr[y] += cnt
            curr[l] -= cnt
        return check(curr) and checkB(ll) and checkB(rr)
```

