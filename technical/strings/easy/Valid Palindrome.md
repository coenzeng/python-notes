---
tags: [string]
title: Valid Palindrome
created: '2021-04-11T18:30:07.483Z'
modified: '2021-04-11T18:39:32.717Z'
---

## Valid Palindrome
:dragon_face: **·** `String` **·** `Easy`

Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Example:
```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

#### Solution 1: Only Aphlanumeric Characters
```python
s = ''.join(x.lower() for x in s if x.isalnum())
return s == s[::-1]
```





