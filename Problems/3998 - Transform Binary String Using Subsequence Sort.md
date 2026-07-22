---
tags:
  - string
  - enumeration
  - greedy
Difficulty Level:
Rating:
Need Review: false
Origin: Weekly 511
First: 2026-07-19
Watch Solution: false
---
[link](https://leetcode.com/problems/transform-binary-string-using-subsequence-sort/description/)
一開始被昨天的逆序對制約，想成1 前面有幾個0 ，
因為1 可以搬到0 的前面，所以我們關注的是：對於每個position，前面有多少個0，如果target 在這個position 的0的數量不夠，代表沒辦法構成。
又，我們知道1可以被往前移，取代掉0，所以0出現是比較理想的狀況，我們在遇到問號要填數字的時候，就優先填0，這個是greedy 的成分。

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

