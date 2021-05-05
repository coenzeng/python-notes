## Fibonacci Number
:panda_face: **·** `Dynamic Programming` **·** `Easy`

Given an integer n, calculate the nth Fibonacci number.
```
F(0) = 0, F(1) = 1 #base cases
F(n) = F(n - 1) + F(n - 2), for n > 1.
```
### Solution 1: Recursion
```python
def fib(n: int) -> int:
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)
```
![](@attachment/Clipboard_2021-04-20-09-01-31.png)

Observe that the leaves on the tree are all fib (1) and fib (0). Those signify the base cases. 
The total number of nodes in the tree will represent the runtime, since each call only does 0 (1) work. Therefore, the number of calls is the runtime. 

**Time Complexity**: How many nodes are in the tree? The root node has two children. Each of those children has two children, and so on. If we do this n times, we'll have roughly O(2^n^) nodes. This gives us a runtime of roughly O(2^n^).

![](@attachment/Clipboard_2021-04-20-09-06-56.png)

**Space Complexity**: O(n), which is the height of the tree. The program must store the recursive function stack, which is at most the height of the tree. Once it reaches a base case, it'll pop that function call off the stack and continue to the other nodes.

### Solution 2: Recursion with Memoization 
There are lots of identical nodes. For example, fib (3) appears twice and fib(2) appears three times. Why should we recompute these from scratch each time? 

In fact, when we call fib(n), we shouldn't have to do much more than 0(n) calls, since there's only O(n) possible values we can throw at fib. Each time we compute fib(i), we should just cache this result in a dictionary and use it later. This is exactly what memoization is. 
```python
def fib(n: int, memo = {}) -> int:
    if n < 2:
        return n
    if n in memo:
        return memo[n]
    else:
        memo[n] = fib(n - 1) + fib(n - 2)
    return memo[n]
```
![](@attachment/Clipboard_2021-04-20-09-15-39.png)

The black boxes represent cached calls that return immediately.

**Time complexity:** How many nodes are in this tree now? The tree now just shoots straight down, to a depth of roughly n. Each node of those nodes has one other child, resulting in roughly 2n children in the tree. This gives us a runtime of O(n). 

**Space complexity:** O(n). 

### Solution 3: Iterative Bottom Up 
```python
def fib(n: int) -> int:
    if n < 2:
        return n
    current = 0
    prev1 = 1 #Starts at F(1)
    prev2 = 0 #Starts at F(0)
    # Since range is exclusive and we want to include N, we need to put n+1.
    for i in range(2, n+1):
        current = prev1 + prev2
        prev2 = prev1
        prev1 = current
    return current
```
We start with fib(0) and fib(1), and we use that to calculate fib(2). We then use fib(1) and fib(2) to calculate fib(3), and so on.

**Time complexity:** O(n). Each value from 2 to N will be visited at least once.

**Space complexity:** O(1). This requires 1 unit of Space for the integer N and 3 units of Space to store the values (curr, prev1 and prev2) for every loop iteration. The amount of Space doesn't change so this has constant Space complexity.

