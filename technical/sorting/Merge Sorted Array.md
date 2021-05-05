---
title: Merge Sorted Array
tags: [sorting]
created: '2021-04-17T18:57:17.783Z'
modified: '2021-04-17T19:02:52.513Z'
---

## Merge Sorted Array
:palm_tree: **·** `Sorting` **·** `Easy`

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

The number of elements initialized in nums1 and nums2 are m and n respectively. You may assume that nums1 has a size equal to m + n such that it has enough space to hold additional elements from nums2.
```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
```
#### Solution 1: Reverse Sorting
```python
def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    #modify nums1 in-place 
    while n > 0:
        if m <= 0 or nums2[n-1] >= nums1[m-1]:  
            nums1[m+n-1] = nums2[n-1]
            n -= 1
        else:
            nums1[m+n-1] = nums1[m-1]
            m -= 1
```

#### Solution 2: Galaxy Brain
```python
def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
    nums1[m:] = nums2
    nums1.sort()
```

