---
tags:
  - "#medium"
  - "#dp"
  - "#array"
Difficulty Level: "#medium"
Rating: 2187
Need Review: true
Origin: 05/07 Daily
First:
Watch Solution: false
---
[Link](https://leetcode.com/problems/jump-game-ix/description/?envType=daily-question&envId=2026-05-07 )

第一眼覺得是union find，但是發現要找到所有的link 可能需要O(n^2) 的時間，於是就改成dp。
two pass，第一次看他前面的，