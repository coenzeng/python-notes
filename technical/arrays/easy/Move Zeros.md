---
tags: [array]
title: Move Zeros
created: '2021-04-10T15:55:07.373Z'
modified: '2021-04-11T03:24:42.227Z'
---

## Move Zeros
:penguin: **·** `Arrays` **·** `Easy`

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

#### Solution 1: Reverse the List
```python
class Solution():
    def moveZeroes(self, nums):
        for index, value in reversed(list(enumerate(nums))):
            if value == 0:
                nums.append(nums.pop(index))
#testing
testcase = Solution()
nums = [0,1,0,3,12]

print(enumerate(nums))
#<enumerate object at 0x00000272017F73C0>

print(list(enumerate(nums)))
#[(0, 0), (1, 1), (2, 0), (3, 3), (4, 12)]

print(reversed(list(enumerate(nums))))
#<list_reverseiterator object at 0x000001B95A0C15B0> 

print(list(reversed(list(enumerate(nums)))))
#[(4, 12), (3, 3), (2, 0), (1, 1), (0, 0)]

testcase.moveZeroes(nums)

print(nums)
#[1, 3, 12, 0, 0]
```
#### Solution 2: Count the Zeroes

```python
count = nums.count(0)
nums[:] = [i for i in nums if i != 0]
nums += [0] * count
```






