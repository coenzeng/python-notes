---
tags: [array]
title: Valid Sudoku
created: '2021-04-11T01:38:50.444Z'
modified: '2021-04-11T03:24:56.969Z'
---

## Valid Sudoku
:penguin: **·** `Arrays` **·** `Medium`

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.

#### Solution 1: 3 Iterations
```python
hash = {}
#check rows
for i in range(len(board)):
    for j in range(len(board[0])):
        if board[i][j] != "." and board[i][j] in hash:
            return False
        else:
            hash[board[i][j]] = 0
    hash = {}
    
#check columns
for i in range(len(board[0])):
    for j in range(len(board)):
        if board[j][i] != "." and board[j][i] in hash:
            return False
        else:
            hash[board[j][i]] = 0
    hash = {}

#check sub-boxes
for box_row in range(0, 9, 3):
    for box_col in range(0, 9, 3):
        for i in range(len(board)//3):
            for j in range(len(board[0])//3):
                if board[box_row + i][box_col + j] != "." and board[box_row + i][box_col + j] in hash:
                    return False
                else:
                    hash[board[box_row + i][box_col + j]] = 0
        
        hash = {}
        
return True
```





