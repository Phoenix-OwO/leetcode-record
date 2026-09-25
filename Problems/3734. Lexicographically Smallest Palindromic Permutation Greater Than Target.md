---
tags:
  - greedy
  - string
Difficulty Level: Hard
Rating: 2300
Need Review: true
Origin: LC 3734
First: November 2, 2025 5:10 PM
Watch Solution: false
---

# 3734. Lexicographically Smallest Palindromic Permutation Greater Than Target

[Link](https://leetcode.com/problems/lexicographically-smallest-palindromic-permutation-greater-than-target/)

**Topics**: Greedy, String

## Notes

和3720. 是一樣的 差在有回文！但注意誰放中間其實就好了

```python
class Solution:
    def lexPalindromicPermutation(self, s: str, target: str) -> str:
        cnt = Counter(s)
        n = len(target)

        mid = ''
        for k, v in cnt.items():
            if v % 2 == 1 and mid == '':
                mid = k
            elif v % 2 == 1:
                return ''
            cnt[k] = cnt[k]//2
        if mid != '' and cnt[mid] == 0:
            del cnt[mid]

        ans = []
        self.res = ''
        def dfs(i):
            if i == n//2:
                curr = ''.join(ans)
                if curr + mid + curr[::-1] > target:
                    self.res = curr + mid + curr[::-1]
                    return True
                return False

            if target[i] in cnt:
                cnt[target[i]] -= 1
                if cnt[target[i]] == 0:
                    del cnt[target[i]]
                ans.append(target[i])
                if dfs(i + 1):
                    return True
                ans.pop()
                cnt[target[i]] += 1
            for k in range(ord(target[i]) + 1, ord('z') + 1):
                if chr(k) in cnt:
                    cnt[chr(k)] -= 1
                    temp = []
                    for key, v in cnt.items():
                        for t in range(v):
                            temp.append(key)
                    ans.append(chr(k))
                    temp.sort()
                    self.res = ''.join(ans) + ''.join(temp) + mid  + ''.join(temp[::-1]) + ''.join(ans[::-1])
                    return True
            return False
        dfs(0)
        return self.res   

        
```