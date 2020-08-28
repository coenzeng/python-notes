# Fizzbuzz

> Write a program that prints the numbers from 1 to 100. For multiples of three print “Fizz” and for multiples of five print “Buzz”. For numbers that are multiples of both three and five print “FizzBuzz”.

```python
for i in range(1, 101):

    if i % 5 == 0 and i % 3 == 0:
        i = "fizzbuzz"
    elif i % 5 == 0:
        i = "buzz"
    elif i % 3 == 0:
        i = "fizz"
    print(i)
```
> What if you're given an list of numbers?
```python
numbers = [45, 22, 14, 65, 97, 72]

for i in range(len(numbers)):

    if i % 5 == 0 and i % 3 == 0:
        numbers[i] = "fizzbuzz"
    elif i % 5 == 0:
        numbers[i] = "buzz"
    elif i % 3 == 0:
         numbers[i] = "fizz"
```
