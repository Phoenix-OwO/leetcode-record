---
tags:
Difficulty Level: Medium
Rating:
Need Review: false
Origin: Biweekly 189
First: 2026-08-15
Watch Solution: false
---
[link](https://leetcode.com/problems/minimum-operations-to-make-a-rotated-palindrome-i/description/)

可以先加起來，就不用一直取餘數
然後有一些細節的小處理，比如先計算好每個chr 的ord ，因為這樣可以省去一點後面的計算功夫。

```python
class Solution:
    def minOperations(self, s: str) -> int:
        n = len(s)
        s += s
        s = [ord(c) - ord('a') for c in s]
        ans = inf 

        if n % 2 == 1:
            for i in range(n//2, n + n // 2):
                curr = i - n//2
                for j in range(1, n//2 + 1):
                    maxC, minC = max(s[i + j], s[i - j]), min(s[i - j], s[i + j])
                    curr += min(maxC - minC, 26 - maxC + minC)
                    if curr > ans:
                        break
                ans = min(ans, curr)
        else:
            for i in range(n//2 - 1, n + n // 2):
                curr = i - n//2 + 1
                for j in range(1, n//2 + 1):
                    maxC, minC = max(s[i + j], s[i - j + 1]), min(s[i + j], s[i - j + 1])
                    curr += min(maxC - minC, 26 - maxC + minC)
                    if curr > ans:
                        break
                ans = min(ans, curr)
        return ans
            

```

