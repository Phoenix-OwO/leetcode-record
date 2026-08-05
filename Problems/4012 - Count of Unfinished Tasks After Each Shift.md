---
tags:
Difficulty Level:
Rating:
Need Review: false
Origin: Weekly 513
First: 2026-08-02
Watch Solution: false
---
[link](https://leetcode.com/problems/count-of-unfinished-tasks-after-each-shift/description/)
基本的binary search 題，概念上大概就是前一場的 remain 加上現在的shift 如果 > 現在所有task 的結尾的時間，就代表所有task 可以在這一輪被完成，這時候我們就重置所有東西，開啟一個新的shift

用bisect_right 是因為小於等於這個值的都可以被算進去，所以要算出來往前推一個（但因為是0-index 所以又不用減）

判定的這邊我一開始只看```shift >= pre[-1] ```後來發現加上remain 可以在同一個if 一起判定。

```python
class Solution:
    def countTasks(self, tasks: List[int], shifts: List[int]) -> List[int]:
        pre = list(accumulate(tasks, initial = 0))
        ans = []
        rem = 0
        n = len(tasks)
        
        for shift in shifts:
            if shift + rem >= pre[-1]:
                rem = 0
                ans.append(0)
            else:
                x = bisect_right(pre, shift + rem)
                ans.append(n + 1 - x)
                rem += shift
        return ans
            
```

