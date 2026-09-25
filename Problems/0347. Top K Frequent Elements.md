---
tags:
  - hashTable
  - heap
  - divideAndConquer
  - counting
Difficulty Level: Medium
Rating:
Need Review: false
Origin:
First: 2026-07-10
Watch Solution: false
---
[link](https://leetcode.com/problems/top-k-frequent-elements/description/)

最簡單寫法：算完出現的次數，sort，然後由小取到大
題目follow up 要求時間複雜度要比nlog(n) 好 
代表我們不能夠去sort這些出現的頻率，注意到：一個數字最多出現n 次，我們可以從多到少的去看他的freq，由大到小的把出現頻率高到低的加進去答案。


```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)
        occur = Counter(nums)
        ans = []
        maxFreq = max(occur.values())
        freq = defaultdict(list)
        for key, value in occur.items():
            freq[value].append(key)
        for i in range(maxFreq, 0, -1):
            if k > 0:
                if len(freq[i]) > 0:
                    ans += freq[i]
                    k -= len(freq[i])
            else:
                return ans
        return ans
```


