---
tags: [linked list]
title: Reverse a Linked List
created: '2021-04-15T01:33:12.114Z'
modified: '2021-04-15T01:43:51.114Z'
---

## Reverse a Linked List
:monkey_face: **·** `Linked List` **·** `Easy`

Given the head of a singly linked list, reverse the list, and return the reversed list.

#### Solution 1: Iterative
```python
def reverseList(self, head: ListNode) -> ListNode:
    prev = None   
    while head:
        curr = head
        head = head.next
        curr.next = prev
        prev = curr        
    return prev
```
#### Solution 2: Recursive
```python
def reverseList(self, head: ListNode) -> ListNode:    
    return self._reverse(head)

def _reverse(self, curr, prev=None):
    if not curr:
        return prev
    n = curr.next
    curr.next = prev
    return self._reverse(n, curr)
```
