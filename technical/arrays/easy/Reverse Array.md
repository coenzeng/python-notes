---
tags: [array, string]
title: Reverse Array
created: '2021-04-11T03:25:21.764Z'
modified: '2021-04-11T03:37:27.698Z'
---

## Reverse Array
:penguin: **·** `Array` **·** `Easy`

Write a function that reverses an array. The input is given as an array of characters s.

#### Solution 1: Slicing
```python
s[:] = s[::-1]
```

#### Solution 2: Reverse
```python
s.reverse()
```

## Reverse String 
:dragon_face: **·** `String` **·** `Easy`
```python
def reverse_string(x):
  return x[::-1]

txt = reverse_string("brooo")
print(txt) #ooorb
```




