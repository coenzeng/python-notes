---
attachments: [Clipboard_2021-04-12-08-45-41.png]
tags: [string]
title: Longest Common Prefix
created: '2021-04-11T19:06:12.694Z'
modified: '2021-04-12T12:45:53.212Z'
---

## Longest Common Prefix
:dragon_face: **·** `String` **·** `Easy`

Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string "".

Example:
```python
Input: strs = ["flower","flow","flight"]
Output: "fl"
```
#### Solution 1: Iteration
```python
if not strs:
    return ""    
shortest = min(strs,key=len)
for index, char in enumerate(shortest):
    for other in strs:
        if other[index] != char:
            return shortest[:index]
return shortest 
```

