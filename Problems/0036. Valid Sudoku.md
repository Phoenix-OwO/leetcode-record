---
tags:
  - array
  - hashTable
  - matrix
Difficulty Level: Medium
Rating: 
Need Review: true
Origin: LC 36
First: April 8, 2025 1:12 PM
Watch Solution: false
---

# 36. Valid Sudoku

[Link](https://leetcode.com/problems/valid-sudoku/solutions/6108715/0-ms-runtime-beats-100-user-code-idea-algorithm-solving-step/?envType=study-plan-v2&envId=top-interview-150)

**Topics**: Array, Hash Table, Matrix

## Notes

很多方法欸 有酷酷的bitmask 法
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        row = defaultdict(int) # key: num, row,  vlaue: cnt 
        col = defaultdict(int) # key: num, col,  value: cnt
        cell = defaultdict(int) # key: num, cell(row, col). value: cnt

        for i in range(9):
            for j in range(9):
                if board[i][j] == '.':
                    continue
                row[(board[i][j], i)] += 1
                col[(board[i][j], j)] += 1
                cell[(board[i][j], i//3, j//3)] += 1
        for v in row.values():
            if v > 1:
                return False
        for v in col.values():
            if v > 1:
                return False
        for v in cell.values():
            if v > 1:
                return False
        return True
```