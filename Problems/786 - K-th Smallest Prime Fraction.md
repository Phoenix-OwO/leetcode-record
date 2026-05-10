---
tags:
  - binarySearch
  - twoPointers
  - sorting
  - heap
Difficulty Level: Medium
Rating: 2168
Need Review: true
Origin: LC 3911 延伸題
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/k-th-smallest-prime-fraction/description/)

很多方法，第三種方法卡卡
方法一：

## 方法一：

```O(n**2 * log(k))```
maintain 一個長度為k 的heap queue

``` python 
class Solution:
    def kthSmallestPrimeFraction(self, arr: List[int], k: int) -> List[int]:
        n = len(arr)
        pq = []
        for i in range(1, n):
            for j in range(i):
                if len(pq) < k:
                    heappush(pq, (-arr[j]/arr[i], arr[j], arr[i]))
                elif -arr[j]/arr[i] > pq[0][0]:
                    _ = heappop(pq)
                    heappush(pq, (-arr[j]/arr[i], arr[j], arr[i]))
                
        return [pq[0][1], pq[0][2]]
```

## 方法二：
活用arr 是排序好的性質
每一排是 ```a[j]``` 分母 分子```a[i]``` 從小排到大，我們只要關心這n - 1 個排頭就好。
時間複雜度  排序排頭```O(nlogn)```，挑k 個 ```O(klogn)```，綜合起來看是```O(max(k, n)logn)```

```python
class Solution:
    def kthSmallestPrimeFraction(self, arr: List[int], k: int) -> List[int]:
        n = len(arr)
        pq = [(arr[0]/arr[i], 0, i) for i in range(1, n)]
        heapify(pq)
        for cnt in range(k - 1):
            _, i, j = heappop(pq)
            if i < j - 1:
                heappush(pq, (arr[i + 1] / arr[j], i + 1, j))
        return [arr[pq[0][1]], arr[pq[0][2]]]
```

## 方法三：
进一步，利用 arr 递增，且每个点对 (i,j) 满足 i<j，我们可以确定 (i,j) 对应的分数  
arr[j]
arr[i]
​
  必然落在 [0,1] 范围内。

假设最终答案  
arr[j]
arr[i]
​
  为 x，那么以 x 为分割点的数轴（该数轴上的点为 arr 所能构造的分数值）上具有「二段性」：

小于等于 x 的值满足：其左边分数值个数小于 k 个；
大于 x 的值不满足：其左边分数值个数小于 k 个（即至少有 k 个）。
而当确定 arr[j] 时，利用 arr 有序，我们可以通过「双指针」快速得知，满足  
arr[j]
arr[i]
​
 <=x 的分子位置在哪（找到最近一个满足  
arr[j]
arr[i]
​
 >x 的位置）。

另外，我们可以在每次 check 的同时，记录下相应的 arr[i] 和 arr[j]。

作者：宫水三叶
链接：https://leetcode.cn/problems/k-th-smallest-prime-fraction/solutions/1127751/gong-shui-san-xie-yi-ti-shuang-jie-you-x-8ymk/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
```