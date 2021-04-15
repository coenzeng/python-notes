---
title: Palindrome Linked List
tags: [linked list]
created: '2021-04-15T12:39:26.728Z'
modified: '2021-04-15T13:12:53.614Z'
---

## Palindrome Linked List
:monkey_face: **·** `Linked List` **·** `Easy`

Given the head of a singly linked list, return true if it is a palindrome.

#### Solution 1: Two Pointers
```python
rev = None # rev (reversed) records the first half
slow = fast = head #slow and fast start at head

while fast and fast.next:
    
    # fast moves twice as fast as slow to the end of the list 
    # if the length is odd, then fast will be last item in list
    # if length is even, then fast will pass the end, becoming None
    fast = fast.next.next

    #populate rev using slow pointer, except rev is reversed
    #rev, rev.next, slow = slow, rev, slow.next
    tmp = rev;
    rev = slow;
    slow = slow.next;
    rev.next = tmp;

if fast:
    #if fast is the last item, then length is odd. Therefore, move slow one step further (cross middle one)
    slow = slow.next

# compare the reversed first half with the second half
while rev and rev.val == slow.val:
    slow = slow.next
    rev = rev.next

# if equivalent then rev become None, return True; otherwise return False 
return not rev
```
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


#### Visualization of Solution 1
s is slow, f is fast, r is rev
```
  1 -> 2 -> 3 -> 2 -> 1
  s
  f
r
```
After first loop is finished
```
1 <- 2 <- 3 -> 2 -> 1
     r    s         f
```
Since f is not None, that means the list is odd, so increment s to skip middle value
```
1 <- 2 <- 3 -> 2 -> 1
     r         s    f
```
After checking r and s nodes are equal while iterating through
```
    1 <- 2 <- 3 -> 2 -> 1
r                       f   s
```
r is None, which means we broke out the loop and this list is a palindrome. 
