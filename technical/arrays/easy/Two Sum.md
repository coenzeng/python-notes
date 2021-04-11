---
tags: [array]
title: Two Sum
created: '2021-04-09T18:10:36.653Z'
modified: '2021-04-11T03:24:54.766Z'
---

## Two Sum
:penguin: **·** `Arrays` **·** `Easy`

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

#### Solution 1: Hash Table
```python
hash = {}
for index, value in enumerate(nums):
    value2 = target - value
    if value2 in hash:
        return [index, hash[value2]]
    else:
        hash[value] = index
```





