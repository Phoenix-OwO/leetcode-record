---
tags:
  - greedy
  - dp
  - twoPointers
Difficulty Level: Medium
Rating:
Need Review: false
Origin: TopInterview150
First: 2026-05-25
Watch Solution: false
---
[link](https://leetcode.com/problems/container-with-most-water/?envType=study-plan-v2&envId=top-interview-150)

greedy 題，但是要怎麼移動pointer ，看要移左邊還是移右邊，這個很重要。
這題吃很多WA
第一個想法：是看```h[l + 1] 跟 h[r - 1]``` 比誰比較大，但這樣的話在這個測資失敗了```[1,2,4,3]```
第二個想法：看誰增加了比較多```min(height[l + 1], height[r]) > min(height[r - 1], height[l])```
但是死在這個測資：```[1,3,2,5,25,24,5]```
看答案的想法：看```h[l] 跟 h[r]```誰比較小，我們把比較小的踢掉。


```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        n = len(height)
        l = 0
        r = n - 1
        area = 0 

        while l < r:
            area = max(area, (r - l) * min(height[r], height[l]))
            if height[l] > height[r]:
                r -= 1
            else:
                l += 1
        return area
```

