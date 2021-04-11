---
tags: [array]
title: Rotate 1D Array
created: '2021-04-10T23:33:10.854Z'
modified: '2021-04-11T03:24:48.013Z'
---

## Rotate 1D Array
:penguin: **·** `Arrays` **·** `Easy`

Given an array, rotate the array to the right by k steps, where k is non-negative.

#### Solution 1: Brute Force
```python
for i in range(k):
    nums.insert(0, nums.pop())
```
#### Solution 2: Triple Reverse
```python
def numReverse(start, end):
    while start < end:
        nums[start], nums[end] = nums[end], nums[start]
        start += 1
        end -= 1

k = k % len(nums)
n = len(nums)

if k:
    numReverse(0, n - 1)
    numReverse(0, k - 1)
    numReverse(k, n - 1)

return nums
```





