---
tags:
Difficulty Level: Hard
Rating: 2150
Need Review: false
Origin: Weekly 513
First: 2026-08-02
Watch Solution: false
---
[link](https://leetcode.com/problems/count-subarrays-with-even-odd-ratio-ii/description/)

看到範圍：覺得一定有個O(nlogn)以下的解法，感覺可以夠過移相來把東西化簡成現在的位置，跟前面的位置，這兩種值，然後再來用可能binary search 的方式找到對應的值。

有了這個想法之後就想著移項，先講最終解法，等等補上一開始的想法。
現在的我們可能叫i 做前面的用j
$$ \frac{x_{i} - x_{j}}{y_{i} - y_{j}} \leq \frac{a}{b}$$ 
經過移項：
$$ (x_{i} - x_{j}) \times b \leq ({y_{i} - y_{j}}) \times a \rightarrow  a \times y_{j} -b \times  x_{j} \leq a \times y_{i} -b \times  x_{i} $$ 
得到結論：對於每個我們遍歷到的position i，我們可以去搜尋前面有幾的j 有符合這個等式- > 可以用binary search 去找出答案。

```python
class Solution:
    def countRatioSubarrays(self, nums: list[int], a: int, b: int) -> int:
        sl = SortedList()
        n = len(nums)
        curr = 0
        ans = 0
        sl.add(0)
        for i in range(n):
            if nums[i] % 2 == 0:
                curr -= b
            else:
                curr += a
            ans += sl.bisect_right(curr)
            sl.add(curr)
        return ans
            
```

