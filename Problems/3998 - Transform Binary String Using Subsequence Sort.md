---
tags:
  - string
  - enumeration
Difficulty Level:
Rating:
Need Review: false
Origin: Weekly 511
First: 2026-07-19
Watch Solution: false
---
[link](https://leetcode.com/problems/transform-binary-string-using-subsequence-sort/description/)

```python
class Solution:
    def transformStr(self, s: str, strs: List[str]) -> List[bool]:
        ans = []
        cntS = defaultdict(int)
        l = len(s)
        inv = []
        curr = 0
        for c in s:
            cntS[c] += 1
            inv.append(cntS['0'])
            
        for i, word in enumerate(strs):
            cntWord = Counter(word)
            if cntWord['1'] + cntWord['?'] < cntS['1'] or cntWord['0'] + cntWord['?'] < cntS['0']:
                ans.append(False)
                continue
            
            cnt0 = 0
            currInv = 0
            rem0 = cntS['0'] - cntWord['0']
            rem1 = cntS['1'] - cntWord['1']
            check = True
            for i, c in enumerate(word):
                if c == '?' and rem0 != 0:
                    c = '0'
                    rem0 -= 1
                elif c == '?':
                    c = '1'
                    rem1 -= 1
                
                if c == '0':
                    cnt0 += 1

                if cnt0 < inv[i]:
                    check = False
                    break
            ans.append(check)
        return ans
            
```

