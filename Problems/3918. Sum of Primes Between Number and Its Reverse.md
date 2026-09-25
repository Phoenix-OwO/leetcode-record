---
tags:
  - math
  - counting
Difficulty Level: Medium
Rating: 1301
Need Review: false
Origin: Weekly 500
First: 2026-05-17
Watch Solution: false
---
[link](https://leetcode.com/problems/sum-of-primes-between-number-and-its-reverse/description/)
預處理質數，用binary search 找出起點，甚至直接看過整個array 都可以


```python
prime = [True]*1001
prime[0] = False
prime[1] = False
p = 2
while p**2 <= 1001:
    if prime[p]:
        for i in range(p * p, 1001, p):
            prime[i] = False
    p += 1

class Solution:
    def sumOfPrimesInRange(self, n: int) -> int:
        rev = int(str(n)[::-1])
        l, r = min(rev, n), max(rev, n)
        ans = 0
        for i in range(l, r + 1):
            if prime[i]:
                ans += i
        return ans
        
```

