---
tags:
Difficulty Level: Medium
Rating: 1700
Need Review: false
Origin:
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/minimize-array-sum-using-divisible-replacements/description/)


## 方法一
方法一就是：每一個數字的倍數，看看有沒有在裡面，這個方法會嚴格受到上界的影響。

```python
class Solution:
    def minArraySum(self, nums: list[int]) -> int:
        nums.sort()
        cnt = Counter(nums)
        MX = max(nums)
        chosen = defaultdict(int)
        ans = 0
        
        for num in nums:
            if cnt[num] == 0:
                continue
            for i in range(num, MX + 1, num):
                ans += cnt[i] * num
                cnt[i] = 0
        return ans            
```

## 方法二
預處理因子，粗略估計：一個數字的因數數量大約是開三次方左右，這樣會比前一個方法快。

```python
MX = 100_001
divisors = [[] for _ in range(MX)]
for i in range(1, MX):
    for j in range(i, MX, i):  # 枚举 i 的倍数 j
        divisors[j].append(i)  # i 是 j 的因子

class Solution:
    def minArraySum(self, nums: list[int]) -> int:
        cnt = Counter(nums)
        ans = 0

        for x, c in cnt.items():  # 遍历 cnt 而不是 nums，这样重复元素只会计算一次
            for d in divisors[x]:  # 从小到大枚举 x 的因子 d
                if d in cnt:
                    ans += d * c  # 把 x 变成 d 是最优的
                    break

        return ans

```

