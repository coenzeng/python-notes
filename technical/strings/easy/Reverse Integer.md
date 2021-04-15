---
tags: [string]
title: Reverse Integer
created: '2021-04-11T04:01:34.556Z'
modified: '2021-04-11T17:11:32.123Z'
---

## Reverse Integer
:dragon_face: **·** `String` **·** `Easy`

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-2^31^, 2^31^ - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

Constraints:

`-2**31 <= x <= 2**31 - 1`

#### Solution 1: Reverse as a String
```python
if x > 0:
    x = int((str(x)[::-1]))
else:
    x = - int(str(abs(x))[::-1])
    
if -2**31 < x <  2**31 - 1:
    return x
else:
    return 0
```





