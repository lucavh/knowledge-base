# Python

## Links
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
- [Python logging basics](https://www.loggly.com/ultimate-guide/python-logging-basics/)

## Formatted strings
```python
print(f"{richestDuck} has a net worth of ${netWorth}.")
>>> Scrooge McDuck has a net worth of $52348493767.5.
```

## Type hinting 
You must list all your required arguments (those WITHOUT default values) before your 
optional arguments (those WITH default values). 

```python
def grapplingHook(direction: float, angle: float, battleCry: str = "") -> None:
    print(f"Direction = {direction}, Angle = {angle}, Battle Cry = {battleCry}")

grapplingHook(angle=90, direction=43.7)
```

Optional type hints:

```python
def addPilot(name: Optional[str] = None):
```

## Context managers

```python
with open('some_file', 'w') as opened_file:
    opened_file.write('Hola!')
```

## Decorators (time_function)
```python
import time
from functools import wraps

def time_function(function):
    
    @wraps(function)
    def inner(*args, **kwargs):
        time_before = time.time()
            
        out = function(*args, **kwargs)
        
        time_after = time.time()
        print(f"{function.__name__} took {time_after - time_before:.2f}s")
        
        return out 
    
    return inner

@time_function    
def my_cooler_algorithm(alpha, beta=1):
    """My cooler algorithm"""
    time.sleep(5 * alpha / beta)

```