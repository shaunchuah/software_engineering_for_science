# Control Flow

Control flow is the order in which individual statements, instructions or function calls of an imperative program are executed or evaluated. The control flow of a Python program is regulated by conditional statements, loops, and function calls.

## Conditional Statements

Conditional statements are used to perform different actions based on different conditions.

### If Statement

An `if` statement is a conditional statement that runs or skips code based on whether a condition is `True` or `False`.

```python
x = 10
if x > 5:
    print("x is greater than 5")
```

### If-Else Statement

An `if-else` statement is a conditional statement that runs one block of code if the condition is `True` and another block of code if it is `False`.

```python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is less than or equal to 5")
```

### If-Elif-Else Statement

An `if-elif-else` statement is a conditional statement that runs different code for different conditions.

```python
x = 10
if x > 5:
    print("x is greater than 5")
elif x == 5:
    print("x is equal to 5")
else:
    print("x is less than 5")
```

### Match Case Statement

Also known as switch-case in other languages. Python 3.10 introduced the `match` statement, which is similar to a `switch` statement in other languages. This is useful when you have multiple conditions to check. Instead of writing a very long `if-elif-else` statement, you can use the `match` statement.

```python

def match_example(x): # we will cover functions in the next section
    match x:
        case 1:
            print("one")
        case 2:
            print("two")
        case _:
            print("other")

match_example(1)
# Output:
# one

match_example(2)
# Output:
# two

match_example(3)
# Output:
# other
```

## Loops

Loops are used to iterate over a sequence or perform a task repeatedly.

### For Loop

A `for` loop is used to iterate over a sequence (list, tuple, dictionary, set, or string).

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits: # 'fruit' is the name we give to each element in the list as we go through the loop
    print(fruit)

# This is equivalent to above:
for x in fruits:
    print(x)

# Output:
# apple
# banana
# cherry
```

!!! tip
    When constructing your loops, try and name the variable a sensible name that helps you understand what the loop is doing.
    For example, if you were looping through a dataframe:
    ```python
    for row in dataframe:
        print(row)
    ```
    This makes it easy to read and understand.

### While Loop

A `while` loop is used to execute a block of code repeatedly as long as a condition is `True`.

```python
i = 1
while i < 6:
    print(i)
    i += 1

# Output:
# 1
# 2
# 3
# 4
# 5
```

## Break and Continue Statements

`break` and `continue` are used to alter the flow of a loop.

### Break Statement

A `break` statement is used to exit a loop when a certain condition is met.

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
    if fruit == "banana":
        break
    
# Output:
# apple
# banana
```

### Continue Statement

A `continue` statement is used to skip the current block and move to the next iteration of the loop.

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    if fruit == "banana":
        continue
    print(fruit)

# Output:
# apple
# cherry
```

## Nested Loops

A nested loop is a loop inside a loop.

```python
adjectives = ["red", "big", "tasty"]
fruits = ["apple", "banana", "cherry"]


for adjective in adjectives:
    for fruit in fruits:
        print(adjective, fruit)

# Output:
# red apple
# red banana
# red cherry
# big apple
# big banana
# big cherry
# tasty apple
# tasty banana
# tasty cherry
```

## List Comprehension

Just to make you aware that list comprehension offers a shorter syntax when you want to create a new list based on the values of an existing list.

!!! warning
    I tend not to recommend this. It is better to be more verbose and explicit in your code, because it is easier for everybody to read and understand. I strongly suggest keeping things as simple as possible. Code is read much more than it is written.

```python
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = [x for x in fruits if "a" in x]

print(newlist)
# Output:
# ['apple', 'banana', 'mango']

# Here is how I would do this instead

newlist = [] # declare you are making a list
for fruit in fruits:
    if "a" in fruit:
        newlist.append(fruit)     

# I think these 3 lines are more readable 
# compared to the shorthand syntax above.
```
