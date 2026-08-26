---
tags:
  - string
  - slidingWindow
Difficulty Level: Medium
Rating: 1483
Need Review: false
Origin: 08/26 Daily
First: 2026-08-26
Watch Solution: false
---
[link](https://leetcode.com/problems/shortest-and-lexicographically-smallest-beautiful-string/description/?envType=daily-question&envId=2026-08-24)

Sliding window 步驟 入窗-> 出窗 -> 更新
因為不想要直接去做字串比較，所以使用int 的方式去存他
關鍵：
To efficiently compare substrings with the same length, I interpret each binary substring as a binary number. For binary strings of equal length, their numerical order is exactly the same as their lexicographical order. Therefore, instead of comparing the substrings character by character, I can simply compare their integer values.

```python
class Solution:
    def shortestBeautifulSubstring(self, s: str, k: int) -> str:
        n = len(s)
        left = 0
        cnt = 0
        ans = inf
        ansIdx = -1
        ansVal = inf
        currVal = 0

        for i in range(n):
            currVal = currVal * 2 + int(s[i])
            cnt += int(s[i])
            while cnt >= k:
                if s[left] == '0':
                    left += 1
                elif cnt > k:
                    currVal -= (2 ** (i - left))
                    left += 1
                    cnt -= 1
                else:
                    break
            if cnt >= k:
                if i - left + 1 < ans:
                    ans = i - left + 1
                    ansIdx = left
                    ansVal = currVal

                elif i - left + 1 == ans:
                    if currVal < ansVal:
                        ansIdx = left
                        ansVal = currVal

        return s[ansIdx: ansIdx + ans] if ans != inf else ''
```

