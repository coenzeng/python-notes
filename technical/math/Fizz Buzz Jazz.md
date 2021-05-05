---
title: Fizz Buzz Jazz
tags: [math]
created: '2021-04-15T14:33:12.604Z'
modified: '2021-04-15T14:37:41.806Z'
---

## Fizz Buzz Jazz
:dragon_face: **·** `Math` **·** `Easy`

Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == "Jazz" if i is divisible by 7.
answer[i] == i if non of the above conditions are true.
answer[i] == a combination of Fizz, Buzz, Jazz depending on what it's divisible by.

#### Solution 1: String Concatenation
```python
def fizzBuzzJazz(self, n: int) -> List[str]:
    list = []   
    for i in range(1, n + 1):
        answer = ""
        if i % 3 == 0:
            answer += "Fizz"
        if i % 5 == 0:
            answer += "Buzz"
        if i % 7 == 0:
            answer += "Jazz"
        if not answer:
            answer = str(i)
        
        list.append(answer)
    return list
```

