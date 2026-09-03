---
tags:
  - numberTheory
  - slidingWindow
Difficulty Level: Medium
Rating: 1750
Need Review: false
Origin: Weekly 516
First: 2026-08-23
Watch Solution: false
---
[link](https://leetcode.com/problems/longest-subarray-with-at-most-k-distinct-prime-factors/description/)
預處理完質數之後就是簡單的sliding window 
要注意的是因為很大的質數也需要記錄自己是自己的質因數，所以在埃氏篩的時候上限要開到max 不可以只開到sqrt(max) 這個量級，不然 > 他的質因數array 裡面會沒有存到自己。

```python
isPrime = [True] * (10 ** 5 + 2)
isPrime[0] = False
isPrime[1] = False

primeF = [[] for _ in range(10 ** 5 + 2)]
for i in range(2, 10 ** 5 + 1):
    if not isPrime[i]:
        continue
    primeF[i].append(i)
    for j in range(i * 2, 10**5 + 1, i):
        isPrime[j] = False
        primeF[j].append(i)

class Solution:
    def longestSubarray(self, nums: list[int], k: int) -> int:
        prime = defaultdict(int)
        l = 0
        ans = 0
        for i, x in enumerate(nums):
            for p in primeF[x]:
                prime[p] += 1
            while len(prime) > k:
                for p in primeF[nums[l]]:
                    prime[p] -= 1
                    if prime[p] == 0:
                        del prime[p]
                l += 1
            if len(prime) <= k:
                ans = max(ans, i - l + 1)
        return ans

        
```

