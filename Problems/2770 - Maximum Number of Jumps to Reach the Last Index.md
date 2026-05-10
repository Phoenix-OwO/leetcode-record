---
tags:
  - dp
  - array
Difficulty Level: Medium
Rating: 1533
Need Review: false
Origin: 05/10 Daily
First: 2026-05-10
Watch Solution: false
---
[link](https://leetcode.com/problems/maximum-number-of-jumps-to-reach-the-last-index/description/?envType=daily-question&envId=2026-05-10)


dp 題 只要他不是- 1 （代表可以踩到）
就可以往後更新所有可以踩到的數字
最後回傳dp[-1]
現在只想知道可不可以時間複雜度小於n 平方