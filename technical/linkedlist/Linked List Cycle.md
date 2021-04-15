---
title: Linked List Cycle
attachments: [Clipboard_2021-04-15-09-37-36.png]
tags: [linked list]
created: '2021-04-15T13:36:28.052Z'
modified: '2021-04-15T13:43:13.100Z'
---

## Linked List Cycle
:monkey_face: **·** `Linked List` **·** `Easy`

Given the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Return true if there is a cycle in the linked list. Otherwise, return false.
<br>
![](@attachment/Clipboard_2021-04-15-09-37-36.png)
```
Input: head = [3,2,0,-4]
Output: true
```
#### Solution 1: Two Pointers
```python
def hasCycle(self, head: ListNode) -> bool:      
    fast = slow = head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
        
        if fast == slow:
            return True
    return False
```
If the linked list has a cycle, the fast and slow pointer will eventually meet. 
