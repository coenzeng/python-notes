---
tags: [string]
title: String to Integer (atoi)
created: '2021-04-13T21:07:30.619Z'
modified: '2021-04-15T01:22:49.194Z'
---

## String to Integer (atoi)
:dragon_face: **·** `String` **·** `Medium`

Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer (similar to C/C++'s atoi function).

1. Ignore any leading whitespace.
2. Check if the next character is '-' or '+'. Read this character in if it is either. This determines if the final result is negative or positive respectively. Assume the result is positive if neither is present.
3. Read in next the characters until the next non-digit charcter or the end of the input is reached. The rest of the string is ignored.
4. Convert these digits into an integer (i.e. "123" -> 123, "0032" -> 32). If no digits were read, then the integer is 0. Change the sign as necessary (from step 2).
5. If the integer is out of the 32-bit signed integer range [-231, 231 - 1], then clamp the integer so that it remains in the range. Specifically, integers less than -231 should be clamped to -231, and integers greater than 231 - 1 should be clamped to 231 - 1.
6. Return the integer as the final result.

Note: Do not ignore any characters other than the leading whitespace and the rest of the string after the digits.

#### Solution 1: 

```python
def myAtoi(s: str) -> int:
    stringlist = list(s.strip()) #remove whitespace, put into a list
    if len(stringlist) == 0:
        return 0
    if stringlist[0] == '-':
        sign = -1
    else:
        sign = 1
    if stringlist[0] in ['-','+']: 
        del stringlist[0]
    value, index = 0, 0
    while index < len(stringlist) and stringlist[index].isdigit():
        value = value*10 + ord(stringlist[index]) - ord('0')
        index += 1
    value *= sign
    value = min(value, 2 ** 31 - 1)
    value = max(-(2 ** 31), value)
    return value
```

`ord(stringlist[index]) - ord('0')` is equal to `int(stringlist[index])`, but int() conversion is slower. `ord('0') == 48`.
