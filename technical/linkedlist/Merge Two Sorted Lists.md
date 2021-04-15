---
tags: [linked list]
title: Merge Two Sorted Lists
created: '2021-04-15T02:07:10.300Z'
modified: '2021-04-15T02:08:47.878Z'
---

## Merge Two Sorted Lists
:monkey_face: **·** `Linked List` **·** `Easy`

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.
```python
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

#### Solution 1: Iterative
```python
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        curr = head = ListNode() #create new linked list
        while l1 and l2:
            if l1.val > l2.val:
                curr.next = l2
                l2 = l2.next
            else:
                curr.next = l1
                l1 = l1.next
            curr = curr.next
        
        curr.next = l1 or l2
        return head.next #since head is 0

```
