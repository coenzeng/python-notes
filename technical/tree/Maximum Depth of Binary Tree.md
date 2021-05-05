---
title: Maximum Depth of Binary Tree
attachments: [Clipboard_2021-04-16-13-57-18.png]
tags: [tree]
created: '2021-04-16T17:51:32.670Z'
modified: '2021-04-16T18:31:20.946Z'
---

# Maximum Depth of Binary Tree
:palm_tree: **·** `Tree` **·** `Easy`

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node to the farthest leaf node.

#### Solution 1: Level Order Traversal
```python
def maxDepth(self, root):
    level = [root] if root else []
    depth = 0
    while level:
        depth += 1 
        queue = []
        for node in level:
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        level = queue
    return depth
```
The queue holds on the nodes in a level, and is reset upon every new level. The loop continues until the final level, when the queue is empty.

```
         10
       /    \
      5     19
    /  \      \
   3    6      21
```

Order of level traversal is 10, 5, 19, 3, 6, 21.

#### Solution 2: Recursion
```python
def maxDepth(self, root):
    if not root:
        return 0

    return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```

#### Recursion Explanation

Let's take an example:
```
         10
       /    \
      5     19
           /
         17
```
We start the algorithm at node 10. Below is pseudocode showing the expansion of the recursive call.
```
# self. maxDepth(None) = 0 by definition, as the base case

self. maxDepth(10)
max(self. maxDepth(5), self. maxDepth(19)) + 1 
max(max(self. maxDepth(None), self. maxDepth(None)) + 1, self. maxDepth(19)) + 1 
max(1, self. maxDepth(19)) + 1 
max(1, max(self. maxDepth(17), self. maxDepth(None)) + 1) + 1 
max(1, max(self. maxDepth(17), 0) + 1) + 1 
max(1, max(max(self. maxDepth(None), self. maxDepth(None)) + 1, 0) + 1) + 1 
max(1, max(max(0, 0) + 1, 0) + 1) + 1 
max(1, max(0 + 1, 0) + 1) + 1
max(1, 1 + 1) + 1 
max(1, 2) + 1
2 + 1 
3
```
