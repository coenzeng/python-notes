---
title: Convert Sorted Array to Binary Search Tree
tags: [tree]
created: '2021-04-17T17:47:36.019Z'
modified: '2021-04-17T18:10:06.137Z'
---

## Convert Sorted Array to Binary Search Tree
:palm_tree: **·** `Tree` **·** `Easy`

Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

#### Solution 1: Recursion
```python
def sortedArrayToBST(self, nums: List[int]) -> TreeNode:

    def convert(left, right):
        if left > right:
            return None
        mid = (left + right) // 2
        node = TreeNode(nums[mid])
        node.left = convert(left, mid - 1)
        node.right = convert(mid + 1, right)
        return node
    return convert(0, len(nums) - 1)
```
Time: O(n), since we iterate through the entire array
Space: O(log n), since the tree is balanced

