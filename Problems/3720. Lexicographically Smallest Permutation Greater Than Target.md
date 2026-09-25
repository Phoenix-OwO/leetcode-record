---
tags:
  - dp
  - string
  - greedy
Difficulty Level: Medium
Rating: 2000
Need Review: true
Origin: LC 3720
First: October 21, 2025 2:41 PM
Watch Solution: false
---

[Link](https://leetcode.com/problems/lexicographically-smallest-permutation-greater-than-target/description/)
就是貪心地先填一樣的，如果沒有一樣的，就只填比他大一點點的，然後這個點以後的全部都由小到大填。


```python
class Solution:
    def lexGreaterPermutation(self, s: str, target: str) -> str:
        cnt = Counter(s)
        ans = []
        self.res = ''
        n = len(target)
        
        def dfs(i:int) -> bool:
            if i == n:
                return False
            if cnt[target[i]] > 0:
                ans.append(target[i])
                cnt[target[i]] -= 1
                if cnt[target[i]] == 0:
                    del cnt[target[i]]
                check = dfs(i+1)
                if check:
                    return True
                cnt[target[i]] += 1
                ans.pop()
                
            for c in range(ord(target[i]) + 1, ord('z') + 1):
                if chr(c) in cnt:
                    ans.append(chr(c))
                    cnt[chr(c)] -= 1
                    temp = []
                    for k, v in cnt.items():
                        for _ in range(v):
                            temp.append(k)
                    self.res = ''.join(ans) + ''.join(sorted(''.join(temp)))
                    return True
            return False
                        
        dfs(0)

        return self.res
```