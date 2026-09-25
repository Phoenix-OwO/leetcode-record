---
tags:
  - dp
  - string
Difficulty Level: Hard
Rating: 1985
Need Review: true
Origin: LC 940
First: July 5, 2025 2:43 PM
Watch Solution: false
---

# 940. Distinct Subsequences II

[Link](https://leetcode.com/problems/distinct-subsequences-ii/solutions/192017/java-c-python-dp-4-lines-o-n-time-o-1-space/)

**Topics**: DP, String

## Notes

一路看從頭開始累積了多少個用dp陣列存起來 我的時間空間都是O(n) 不過 可以修改成時間O(26n) 空間O(1) 因為只要存26字母

260907更新：時間O(n)就夠了 用curr 存目前的字串的總數，然後扣掉目前的 以這個字母結尾的

```python
class Solution:
    def distinctSubseqII(self, s: str) -> int:
        MOD = 10**9 + 7
        n = len(s)
        cnt = defaultdict(int)
        curr = 1
        
        for c in s:
            tmp = curr - cnt[c]
            cnt[c] = curr
            curr += tmp
            curr %= MOD
        return sum(cnt.values()) % MOD
```