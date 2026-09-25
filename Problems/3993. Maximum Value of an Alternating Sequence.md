---
tags:
Difficulty Level: Medium
Rating:
Need Review: true
Origin: Biweekly 187
First: 2026-07-18
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-value-of-an-alternating-sequence/)
題目要求找最大，注意到他要altenative，所以一定要減少又增加，因為跟隔壁的差值最多是m，所以裡想的做法就是每次加m之後減ㄧ。就是+m, -1, +m, -1
想法：因為是找最大的值，所以我們可以不管最後的剪一，因此採用下面的寫法，
在思考時漏掉n == 1 這個狀況，因為這樣的話就只會有s本人，沒有加減。
此外也要思考奇數跟偶數的狀況，我覺得是個細心題，要記得複習重新想一次。

```python
class Solution:
    def maximumValue(self, n: int, s: int, m: int) -> int:
        if n == 1:
            return s
        return s + m * (n // 2) - (n - 2)//2
```

