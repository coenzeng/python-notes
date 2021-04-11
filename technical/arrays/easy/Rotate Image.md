---
tags: [array]
title: Rotate Image
created: '2021-04-11T01:20:45.562Z'
modified: '2021-04-11T03:24:49.271Z'
---

## Rotate Image 
:penguin: **·** `Arrays` **·** `Easy`

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

#### Solution 1: Flip, then Transpose
```python
class Solution:
    def rotate(self, A):
        A[:] = zip(*A[::-1])
```
`[::-1]` flips the matrix upside down, `zip` transposes it.
`*` expands the list and passes its elements to the function.

##### Clockwise rotate:
First flip upside down, then transpose.
```python
1 2 3     7 8 9     7 4 1
4 5 6  => 4 5 6  => 8 5 2
7 8 9     1 2 3     9 6 3
```
##### Anticlockwise rotate:
First transpose, then flip upside down. 
```python
class Solution:
    def rotate(self, A):
        A[:] = list(zip(*A))[::-1]
```






