# Functions

Functions are reusable blocks of code that can be called with a set of arguments. They are defined using the `def` keyword, followed by the function name, a list of arguments in parentheses, and a colon. The function body is indented.

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")

# Output:
# Hello, Alice!
```

## Returns

Functions can return a value using the `return` keyword. If no return value is specified, the function returns `None`.

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)

# Output:
# 5
```

## Default Arguments

Functions can have default arguments, which are used when the argument is not provided.

```python
def greet(name="world"):
    print(f"Hello, {name}!")

greet()

# Output:
# Hello, world!
```

## Pythons args and kwargs

Functions in Python can accept a variable number of arguments using the special `*args` and `**kwargs` syntax.

Conventionally in Python, `*args` refers to positional arguments, while `**kwargs` refers to keyword arguments. `*args` is a tuple of the positional arguments, while `**kwargs` is a dictionary of the keyword arguments.

```python
def add(*args):
    return sum(args)

result = add(1, 2, 3, 4)
print(result)

# Output:
# 10

def greet(**kwargs):
    if "name" in kwargs:
        print(f"Hello, {kwargs['name']}!")
    else:
        print("Hello, world!")

greet(name="Alice")

# Output:
# Hello, Alice!
```

For an in-depth explanation of `*args` and `**kwargs`, see <https://www.geeksforgeeks.org/args-kwargs-python/>.

## Functions Within Functions

Functions can be defined inside other functions, and can capture variables from the enclosing scope.

```python
def outer():
    x = 1
    def inner():
        return x 
        # this x variable comes from above, ie. this block of 
        # code can access the context from outside the function
    return inner()

result = outer()
print(result)

# Output:
# 1
```

## Passing Functions into Functions

Functions are first-class citizens in
Python, which means they can be passed as arguments to other functions.

```python
def apply(func, value):
    return func(value)

def double(x):
    return 2 * x

result = apply(double, 3)
print(result)

# Output:
# 6
```

## Advanced Techniques

### Lambda Expressions/Anonymous Functions

Functions can also be defined using lambda expressions, which are anonymous functions. This is usually only used when functions are very simple and commonly used in pandas to apply simple transformations to dataframes.

```python
double = lambda x: 2 * x

result = double(3)
print(result)

# Output:
# 6
```

### Type Hints and Annotations

Functions can be defined with type hints to specify the types of the arguments and return value. This is not enforced by Python, but can be used by type checkers and IDEs to provide additional information. For example, in VSCode you can hover over a function to see the types of the arguments and return value. The value of this is when you are using complex functions and helps prevent passing the wrong datatypes to functions.

```python
def add(a: int, b: int) -> int:
    return a + b

result = add(2, 3)
print(result)

# Output:
# 5
```

### Docstrings

Functions can be defined with docstrings to provide documentation. In VSCode, you can hover over a function to see the docstring. This is useful for documenting what your function does.

```python
def greet(name):
    """
    This function greets the given name.
    """
    print(f"Hello, {name}!")

help(greet)

# Output:
# Help on function greet in module __main__:
#
# greet(name)
#     This function greets the given name.
```
