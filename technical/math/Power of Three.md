---
title: Power of Three
tags: [math]
created: '2021-04-15T16:31:21.821Z'
modified: '2021-04-15T16:54:15.052Z'
---

## Power of Three
:tropical_fish: **·** `Math` **·** `Easy`

Given an integer n, return true if it is a power of three. Otherwise, return false.

An integer n is a power of three, if there exists an integer x such that n == 3^x^.

#### Solution 1: Iteration
```python
def isPowerOfThree(n: int) -> bool:
    if n < 1:
        return False
    while n % 3 == 0:
        n /= 3
    return n == 1
```
One simple way of finding out if a number n is a power of a number b is to keep dividing n by b as long as the remainder is 0. This is because

n = b^x^
n = b × b × … × b 
​	
Hence it should be possible to divide `n` by `b` `x` times, every time with a remainder of 0 and the end result to be 1.

Time: O(log~b~(n)). In this case O(log~3~(n)). The number of divisions is given by that logarithm.

Space: O(1)

