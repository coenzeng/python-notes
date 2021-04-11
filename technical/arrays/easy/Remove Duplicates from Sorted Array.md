---
tags: [array, Easy]
title: Remove Duplicates from Sorted Array
created: '2021-04-08T20:24:33.458Z'
modified: '2021-04-11T03:24:45.870Z'
---

## Remove Duplicates from Sorted Array
:penguin: **·** `Arrays` **·** `Easy`

Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

Clarification:

Note that the input array is passed in by reference, which means a modification to the input array will be known to the caller as well.

#### Solution 1: Two Pointer
```python
i = 0
while i < len(nums) - 1: 
    if nums[i] == nums[i + 1]:
        nums.pop(i)
        i -= 1
    i += 1
return len(nums)
```

#### Solution 2: Set, then Sort
```python
nums[:] = sorted(set(nums))
return len(nums)
```


