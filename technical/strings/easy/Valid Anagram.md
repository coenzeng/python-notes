---
tags: [string]
title: Valid Anagram
created: '2021-04-11T18:05:38.475Z'
modified: '2021-04-11T18:10:41.947Z'
---

## Valid Anagram
:dragon_face: **·** `String` **·** `Easy`

Given two strings `s` and `t`, return true if `t` is an anagram of `s`, and false otherwise.

#### Solution 1: Two Hash Tables
```python
hash1 = {}
hash2 = {} 
for value in s:
    hash1[value] = hash1.get(value, 0) + 1   
for value in t:
    hash2[value] = hash2.get(value, 0) + 1

return hash1 == hash2
```
#### Solution 2: One Hash Table
```python
hash = {}
for value in s:
    hash[value] = hash.get(value, 0) + 1   
for value in t:
    hash[value] = hash.get(value, 0) - 1

for key, value in hash.items():
    if value != 0:
        return False
return True





