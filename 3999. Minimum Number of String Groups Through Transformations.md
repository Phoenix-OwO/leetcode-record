---
tags:
  - string
  - enumeration
Difficulty Level: Hard
Rating:
Need Review: true
Origin: Weekly 511
First: 2026-07-19
Watch Solution: true
---
[link](https://leetcode.com/problems/minimum-number-of-string-groups-through-transformations/description/)


```python
class Solution:
    def minimumGroups(self, words: List[str]) -> int:
        def booth(s):
            ss = s + s
            n = len(s)
        
            i = 0
            j = 1
            k = 0
        
            while i < n and j < n and k < n:
                if ss[i+k] == ss[j+k]:
                    k += 1
                    continue
        
                if ss[i+k] > ss[j+k]:
                    i = i + k + 1
                    if i <= j:
                        i = j + 1
                else:
                    j = j + k + 1
                    if j <= i:
                        j = i + 1
                k = 0
        
            pos = min(i, j)
            return ss[pos:pos+n]
        cnt = defaultdict(int)
        for w in words:
            even = []
            odd = []
            for i, c in enumerate(w):
                if i % 2 == 0:
                    even.append(c)
                else:
                    odd.append(c)

            minE = booth(''.join(even))
            minO = booth(''.join(odd))
            cnt[(minE, minO)] += 1
        # print(cnt)
        return len(cnt)
            
```

