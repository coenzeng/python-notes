---
title: Count Primes
attachments: [Clipboard_2021-04-15-15-37-09.png, Clipboard_2021-04-15-15-39-16.png, Clipboard_2021-04-15-15-41-25.png]
tags: [math]
created: '2021-04-15T19:33:55.781Z'
modified: '2021-04-15T19:54:29.670Z'
---

## Count Primes
:tropical_fish: **·** `Math` **·** `Easy`

Count the number of prime numbers less than a non-negative number, `n`.

#### Solution 1: Sieve of Eratosthenes
```python
def countPrimes(self, n):
    if n < 3:
        return 0
    primes = [True] * n
    primes[0] = primes[1] = False
    for i in range(2, int(n ** 0.5) + 1):
        if primes[i]:
            for j in range(i * i, n, i):
                primes[j] = False
    return sum(primes)
```
#### The Sieve of Eratosthenes Algorithm
Suppose we are required to count the number of primes that less than 21. Start by creating an array that contains 21 integers.
![](@attachment/Clipboard_2021-04-15-15-37-09.png)

Now, let's start with 2, the smallest prime number. We mark the multiples of this number as non-primes in the array by setting it to `False`.

![](@attachment/Clipboard_2021-04-15-15-39-16.png)

Move on to 3, the next prime number. Mark all multiples of 3 as `False`.

![](@attachment/Clipboard_2021-04-15-15-41-25.png)

All the numbers not marked are primes. What are the bounds of the first loop? The outer loop will start at `2` and go up to `sqrt(n)`. This is because by that point we will have considered all of the possible multiples of all the prime numbers below n.

Say the index we picked from the outer loop is `i`, then the inner loop will start at `i*i` and increase by increments of `i` until it surpasses `n`.

But why start at `i * i`? Why not start at `2*i` to keep things simple? Basically, the prime numbers smaller than i would have already covered the multiples smaller than `i*i`. Let's take a look at the prime number 7 to see how all the multiples up to `7*7` are already covered by primes smaller than '7'.
```
7 * 2 = 14 = 2 * 7
7 * 3 = 21 = 3 * 7
7 * 4 = 28 = 2 * 2 * 7 = 2 * 14
7 * 5 = 35 = 5 * 7
7 * 6 = 42 = 2 * 3 * 7 = 2 * 21
```
Finally, return the count of `True` values in the array, which represent the prime numbers. 
