# Reverse a string.
### Option 1: Slicing
```python
def reverse_string(x):
  return x[::-1]
  
string = reverse_string("Hello Coen")
print(string)
```
#### Simplified version
```python
string = "Hello Coen"
print(string[::-1])
```

### Option 2: Reversed and join
```python
string = "Hello Coen"
print("".join(reversed(string)))

```
### Option 3: Loop (don't use)
```python
string = "Hello Coen"
reversed_string = []
index = len(string)

while index > 0:
  reversed_string = string[-1]
  index -= 1
print(reversed_string)
```
