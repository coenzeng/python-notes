---
tags: [array]
title: Intersection of Two Arrays II
created: '2021-04-11T00:59:45.841Z'
modified: '2021-04-11T03:24:37.978Z'
---

## Intersection of Two Arrays II
:penguin: **·** `Arrays` **·** `Easy`

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

You can return the answer in any order.

#### Solution 1: Hash Table
```python
hash = {}
intersection = []

for value in nums1:
    hash[value] = hash.get(value, 0) + 1
    
for value in nums2:
    if value in hash:
        intersection.append(value)
        hash[value] -= 1
        
        if hash[value] == 0:
            hash.pop(value)
            
return intersection
```

 #### Solution 2: Two Pointer
```python       
n1, n2, intersection = sorted(nums1), sorted(nums2), []
p1 = p2 = 0
while p1 < len(n1) and p2 < len(n2):
    if n1[p1] < n2[p2]:
        p1 += 1
    elif n2[p2] < n1[p1]:
        p2 += 1
    else:
        intersection.append(n1[p1])
        p1 += 1
        p2 += 1
return intersection
```





