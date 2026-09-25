---
tags:
  - array
  - hashTable
  - math
  - binarySearch
  - combinatorics
Difficulty Level: Hard
Rating: 2532
Need Review: true
Origin: 07/17 Daily
First: 2026-07-17
Watch Solution: false
---
[link](https://leetcode.com/problems/sorted-gcd-pair-queries/description/?envType=daily-question&envId=2026-07-18)

這題很多概念，包括容斥、由後往前推，還有binary search 去找答案（最簡單的一步）

思考流程：
1. 因為數量級是10 的5次，所以我們可以用counting sort 去找到每一個數字對應到幾個sub sequence，再用binary search 找答案
2. 對於每個1 ~ 10^5 的數字，我們想要計算有幾個pair 的GCD，而且要有效率，先用2 來想 -> 想到可以計算有幾個數字是2 的倍數，然後我們就C幾取2 這樣，但是這樣會算到很多不符合的組合，比如4, 4 或是 12, 24 這種最大公因數根本不是2 的，所以我們要想辦法扣掉重複算的這些。
3. 觀察到對於2 所有GCD 是2 的倍數（不含2）的pair 應該被扣掉-> 我們應該先算比較大的數字的pairs，這樣再扣的時候可以省去一些體力
4. 前面提到要計算這個array 裡面是2 的倍數有幾個，所以我們就，暴力算一下，列舉一下2, 4, 6, ... 等數字在裡面出現幾次之後再加起來。
5. 當我們做好前置作業，就可以開始計算每一個GCD pair 出現幾次了，由10^5 往前推，針對每個數字去計算GCD 是他的 pairs 有多少個，

```python
class Solution:
    def gcdValues(self, nums: List[int], queries: List[int]) -> List[int]:
        ans = []
        n = len(nums)
        maxNum = max(nums)
        mulCnt = defaultdict(int)
        gcdCnt = [0] * (maxNum + 1)
        gcdAcc = []
        freq = Counter(nums)

        for d in range(1, maxNum + 1):
            for multiple in range(d, maxNum + 1, d):
                mulCnt[d] += freq[multiple]

        for i in range(maxNum, 1, -1):
            gcdCnt[i] = (mulCnt[i] * (mulCnt[i] - 1))//2
            for j in range(2, maxNum // 2 + 1):
                if i * j > maxNum:
                    break
                gcdCnt[i] -= gcdCnt[i * j]
        gcdCnt[1] = (n * (n - 1)) // 2 - sum(gcdCnt)

        curr = 0
        for i in range(1, maxNum + 1):
            curr += gcdCnt[i]
            gcdAcc.append(curr)
        
        for q in queries:
            ans.append(bisect_right(gcdAcc, q) + 1)

        return ans
```

