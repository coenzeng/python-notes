---
title: Roman to Integer
tags: [math]
created: '2021-04-15T17:56:15.909Z'
modified: '2021-04-15T18:03:04.218Z'
---

## Roman to Integer
:tropical_fish: **·** `Math` **·** `Easy`

Given a roman numeral, convert it to an integer.
```
Symbol       Value
I            1
V            5
X            10
L            50
C            100
D            500
M            1000
```
There are six instances where subtraction is used:
* `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
* `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
*  `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

#### Solution 1: Hash Table
```python
def romanToInt(self, s):
    roman = {'M': 1000,'D': 500 ,'C': 100,'L': 50,'X': 10,'V': 5,'I': 1}
    value = 0
    
    for index in range(0, len(s) - 1):
        if roman[s[index]] < roman[s[index + 1]]:
            value -= roman[s[index]]
        else:
            value += roman[s[index]]
    value += roman[s[-1]]
    return value
```
If a letter is less than its latter one, this letter is subtracted, except for the last one. The last letter is always added. 

Time: O(n)
Space: O(1), since the hash table is a fixed size.

