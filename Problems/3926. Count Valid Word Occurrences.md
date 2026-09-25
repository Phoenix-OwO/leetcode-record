---
tags:
Difficulty Level: Medium
Rating: 1600
Need Review: false
Origin:
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/count-valid-word-occurrences/description/)
分組循環

```python
class Solution:
    def countWordOccurrences(self, chunks: list[str], queries: list[str]) -> list[int]:
        s = ''.join(chunks)
        cnt = defaultdict(int)

        for t in s.split():  # 不用 split 的写法见另一份代码
            n = len(t)
            i = 0
            while i < n:
                if t[i] == '-':
                    i += 1
                    continue
                start = i
                # 遇到 "--"（连续两个 '-'）就跳出循环
                while i < n and (t[i] != '-' or i < n - 1 and t[i + 1] != '-'):
                    i += 1
                cnt[t[start: i]] += 1

        return [cnt[q] for q in queries]


```