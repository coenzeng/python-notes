---
tags: [array]
title: Single Number
created: '2021-04-09T16:23:32.561Z'
modified: '2021-04-11T03:24:50.866Z'
---

## Single Number
:penguin: **·** `Arrays` **·** `Easy`

Given an array of integers nums, every element appears twice except for one. Find that single one.

#### Solution 1: Hash Table
```python
hash = {}
for value in nums:
    hash[value] = hash.get(value, 0) + 1
    
for key, value in hash.items():
    if value == 1:
        return key
```

#### Solution 2: Bitwise XOR 
```python
result = 0
for value in nums:
    result ^= value
return result
```
#### Solution 3: Math Trick
```python
return 2*sum(set(nums)) - sum(nums)
```


