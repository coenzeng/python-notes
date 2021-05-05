## First Bad Version
:palm_tree: **·** `Searching` **·** `Easy`

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

#### Solution 1: Binary Search
```python
def firstBadVersion(self, n):
    left = 1
    right = n 
    
    while left < right:
        mid = (left + right)//2 #// insures an integer
        
        if isBadVersion(mid) == False:
            left = mid + 1
        else:
            right = mid 
        
    return left
```
Time complexity : O(log n). The search space is halved each time.

Space complexity : O(1).
```
Scenario #1: isBadVersion(mid) => false

 1 2 3 4 5 6 7 8 9
 G G G G G G B B B       G = Good, B = Bad
 |       |       |
left    mid    right
```
Let us look at the first scenario above where `isBadVersion(mid)⇒false`. We know that all versions preceding and including midmid are all good. So we set `left=mid+1` to indicate that the new search space is the interval `[mid+1,right]` (inclusive).
```
Scenario #2: isBadVersion(mid) => true

 1 2 3 4 5 6 7 8 9
 G G G B B B B B B       G = Good, B = Bad
 |       |       |
left    mid    right
```
The only scenario left is where `isBadVersion(mid)⇒true`. This tells us that mid **may or may not** be the first bad version, but we can tell for sure that all versions after mid can be discarded. Therefore we set `right = mid` as the new search space of interval `[left,mid]`(inclusive).

How can you tell for sure that left and right eventually meet and that it's the first bad version? During an interview, test for a size of input 2. If it reduces the search space to a the correct single element, then algorithm is correct. If we wanted to find the **last good** version, then we change the code to `left = mid` and `right = mid - 1`.
