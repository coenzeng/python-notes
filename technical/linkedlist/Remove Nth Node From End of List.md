---
attachments: [Clipboard_2021-04-14-21-45-53.png]
tags: [linked list]
title: Remove Nth Node From End of List
created: '2021-04-15T01:45:02.120Z'
modified: '2021-04-15T02:02:44.002Z'
---

## Remove Nth Node From End of List
:monkey_face: **·** `Linked List` **·** `Easy`

Given the head of a linked list, remove the nth node from the end of the list and return its head.


![](@attachment/Clipboard_2021-04-14-21-45-53.png)
```python
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```
#### Solution 1: Two Pointers
```python
def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
    fast = slow = head
    
    for _ in range(n):
        fast = fast.next
    
    if not fast:
        return head.next
    #fast = None only when n = length of list 
    #this means just remove the head
    
    while fast.next:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return head
```
