---
tags:
  - hashTable
  - greedy
  - sorting
Difficulty Level: Hard
Rating: 2362
Need Review: true
Origin: 09/18 Daily
First: 2026-09-18
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-number-of-non-overlapping-substrings/description/?envType=daily-question&envId=2026-09-12) 思考題！
一開始的想法是猜記錄每個字母出現的頭尾，然後就是non-overlap interval類型的題目，但發現這兩種case 在non overlapping interval 題型會是一樣的case ababa abbba ，但是這這題是不一樣的，Case1 選b 要選到兩端，但是case 2 選b 只要選中間三個。
新想法：我們需要去計算對於每一個字母，如果想要選他，我們應該要選到多長的區段，這塊是這題的精華，也就是greedy的所在，
我們可以貪婪地往左右長這個區間（對於每個字母至多O(n) 的時間複雜度，所以最多就是O(26n))，想到這個之後就解決了
之後就是sort interval、把它當成一般的non-overlapping intervals 問題處理即可

```python
class Solution:
    def maxNumOfSubstrings(self, s: str) -> list[str]:
        n = len(s)
        start = {}
        end = {}
        for i, x in enumerate(s):
            if x not in start:
                start[x] = i
            end[x] = i
        
        newInt = []
        for ch in start.keys():
            l, r = start[ch], start[ch]
            minLeft, maxRight = start[ch], end[ch]
            while l >= minLeft or r <= maxRight:
                if r <= maxRight:
                    minLeft = min(minLeft, start[s[r]])
                    maxRight = max(maxRight, end[s[r]])
                    r += 1
                if l >= minLeft:
                    minLeft = min(minLeft, start[s[l]])
                    maxRight = max(maxRight, end[s[l]])
                    l -= 1
            newInt.append((minLeft, maxRight))
        
        newInt = sorted(newInt, key = lambda x: x[1])
        currS, currE = newInt[0][0], newInt[0][1]
        ans = [s[currS: currE + 1]]
        for newS, newE in newInt[1:]:
            if newS <= currE:
                continue
            else:
                ans.append(s[newS: newE + 1])
                currS, currE = newS, newE
        return ans

```

