# Binary Tree Level Order Traversal (BFS)
:palm_tree: **·** `Tree` **·** `Easy`

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

```
Example:
         10
       /    \
      5     19
    /  \      \
   3    6      21
   
Output: [[10], [5, 19], [3, 6, 21]]
```
#### Solution 1: Level Order Traversal
```python
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        level = [root] if root else []
        answer = []
    
        while level:
            nextLevel = []
            row = []
            for node in level:
                row.append(node.val)
                if node.left:
                    nextLevel.append(node.left)
                if node.right:
                    nextLevel.append(node.right)
            level = nextLevel
            if row: #don't append last row since it will be empty
                answer.append(row)
        return answer
```
