---
title: Validate Binary Search Tree
attachments: [Clipboard_2021-04-17-11-40-50.png, Clipboard_2021-04-17-11-53-21.png, Clipboard_2021-04-17-12-40-43.png]
tags: [tree]
created: '2021-04-17T14:53:54.398Z'
modified: '2021-04-17T16:42:36.111Z'
---

## Validate Binary Search Tree
:palm_tree: **·** `Tree` **·** `Easy`

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:
* The left subtree of a node contains only nodes with keys less than the node's key.
* The right subtree of a node contains only nodes with keys greater than the node's key.
* Both the left and right subtrees must also be binary search trees.

![](@attachment/Clipboard_2021-04-17-11-40-50.png)
#### Solution 1: Recursive Traversal
```python
def isValidBST(self, root, floor=float('-inf'), ceiling=float('inf')):
    # Empty trees are valid BSTs.
    if not root: 
        return True
    # The current node's value must be between floor and ceiling.
    if root.val <= floor or root.val >= ceiling:
        return False
    # in the left branch, root is the new ceiling
    # contrarily root is the new floor in right branch
    return self.isValidBST(root.left, floor, root.val) and 
           self.isValidBST(root.right, root.val, ceiling)
```
#### Solution 2: Iterative Traversal with a Stack
```python
if not root:
    return True

stack = [(root, float(-inf), float(inf))]
while stack:
    root, lower, upper = stack.pop()
    if not root:
        continue
    val = root.val
    if val <= lower or val >= upper:
        return False
    stack.append((root.right, val, upper))
    stack.append((root.left, lower, val))
return True
```

#### Solution 3: Iterative Inorder Traversal
![](@attachment/Clipboard_2021-04-17-11-53-21.png)
The top picture shows nodes numbered in the order visited. Using DFS inorder (`Left -> Node -> Right`) for a valid BST, each element should be smaller than the next one.
![](@attachment/Clipboard_2021-04-17-12-40-43.png)
```python
def isValidBST(self, root: TreeNode) -> bool:
    stack, prev = []
    prev = float(-inf)

    while stack or root:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        
        # next element must be larger than the previous
        if root.val <= prev:
            return False
        prev = root.val
        root = root.right

    return True
```
Explanation:
```
    2
  /   \
 1     3
 ```
 1. Inorder traversal starts that the leftmost node (node.val=1). It gets there by starting at the root and iterating to the leftmost node using the while loop:  
 ```python
while root:
  stack.append(root)
  root = root.left
```
2. It pops the leftmost node (node 1) and sets that equal to root. it checks if root.val is less than prev, which on the first iteration `prev = -infinity` so it must be false.
``` 
# End of First iteration:
stack at the beginning == [node 2, node 1]
stack at the end == [node 2]
prev == 1
root == None
```
3. Starting the second iteration, stack is True, but root is False. Since root is False, it doesn't enter the `while root` loop. This occurs when both left and right nodes have been checked, so the stack moves up a node. 
```
#End of Second iteration:
stack at beginning == [node 2]
stack at end == [None]
prev == 2
root == TreeNode{val: 3, left: None, right: None}
```

```
#End of Third iteration:
stack at beginning == [node 3]
stack at end == [None]
prev == 3
root == None
```
Now that both the stack and root are False, the while loop exits and thus the function returns true. 

#### Solution 4: Recursive Inorder Traversal
```python
def isValidBST(self, root: TreeNode) -> bool:

    def inorder(root):
        if not root:
            return True
        if not inorder(root.left):
            return False
        if root.val <= self.prev:
            return False
        self.prev = root.val
        return inorder(root.right)

    self.prev = float(-inf)
    return inorder(root)
```
Time Complexity: O(n). For inorder traversal, worst case is O(n), where the problem node is the rightmost node. 
Space Complexity: O(n), since we keep up with the entire tree.




