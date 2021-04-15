## First Unique Character in a String
:dragon_face: **·** `String` **·** `Easy`

Given a string `s`, return the first non-repeating character in it and return its index. If it does not exist, return  `-1`.

#### Solution 1: Hash Table
```python
hash = {}
for value in s: 
    hash[value] = hash.get(value, 0) + 1
          
for index, value in enumerate(s):
    if hash[value] == 1:
        return index

return -1
```




