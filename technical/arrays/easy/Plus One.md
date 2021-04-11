---
tags: [array]
title: Plus One
created: '2021-04-10T20:10:23.210Z'
modified: '2021-04-11T03:24:44.287Z'
---

## Plus One 
:penguin: **·** `Arrays` **·** `Easy`

Given a non-empty array of decimal digits representing a non-negative integer, increment one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

#### Solution 1: Convert Array to Int
```python
number = "".join(str(value) for value in digits)
number = int(number) + 1
digits = [i for i in str(number)]
return digits
```

#### Solution 2: Recursion
```python
def plusOne(self, digits):
    digits = digits or [0] #in case of [9], an empty list will be [0]
    last = digits.pop()
    
    if last == 9:
        return self.plusOne(digits) + [0]
    else:
        return digits + [last + 1]
```



