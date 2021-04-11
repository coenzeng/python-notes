## Contains Duplicate
:penguin: **·** `Arrays` **·** `Easy`

Given an integer array nums, return `true` if any value appears at least twice in the array and return `false` if every element is distinct.

#### Solution 1: Hash Table
```python
hash = {}
for value in nums:
    if value not in hash:
        hash[value] = 0
    else:
        return True
return False
```

#### Solution 2: Infinity Brain
```python
return len(nums) != len(set(nums))
```

