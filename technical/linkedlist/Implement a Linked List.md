## Implement a Linked List
:monkey_face: **·** `Linked List` **·** `Easy`

```python
class ListNode:
    def __init__(self, value=0):
        self.value = value
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
    
    def at_beginning(self, new_value):
        new_node = ListNode(new_value)
        new_node.next = self.head
        self.head = new_node

    def at_end(self, new_value):
        new_node = ListNode(new_value)
        if self.head is None:
            self.head = new_node
            return
        last = self.head
        while(last.next):
            last = last.next
        last.next=new_node

    def print_list(self):
        value = self.head
        while value is not None:
            print(value.value)
            value = value.next

    def reverse(self):
        prev = None
        head = self.head
        while head:
            curr = head
            head = head.next
            curr.next = prev
            prev = curr
        self.head = prev

list = LinkedList()
list.at_end("Mon")
list.at_end("Tues")
list.at_end("Wedn")
list.reverse()
list.print_list() #Output:
#Wedn
#Tues
#Mon

```
