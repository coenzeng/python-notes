---
title: Symmetric Tree
attachments: [Clipboard_2021-04-17-14-12-10.png]
tags: [tree]
created: '2021-04-17T17:06:07.530Z'
modified: '2021-04-17T18:13:45.179Z'
---

## Symmetric Tree
:palm_tree: **·** `Tree` **·** `Easy`

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).


#### Solution 1: Level Order Traversal
```python
def isSymmetric(self, root: TreeNode) -> bool:
    level = [root] if root else []

    while level:
        queue = []
        queue_value = []
        for node in level:
            if node.right:
                queue.append(node.right)
                queue_value.append(node.right.val)
            else:
                queue_value.append(None)
            if node.left:
                queue.append(node.left)
                queue_value.append(node.left.val)
            else:
                queue_value.append(None)
            
        if queue_value != queue_value[::-1]:
            return False
        level = queue      

    return True
```
Time: O(n), since we traverse the entire tree once
Space: O(n). In the worst case, we have to insert n nodes in the queue

