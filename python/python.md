# Python

## Cohesion & coupling

- Cohesion & coupling are software quality metrics
- Cohesion is the degree to which elements of a certain class or function belong together.
  - Weak cohesion: function does a lot of different things that do not belong together
  - Strong cohesion: clear responsibility, only one task to execute
- Coupling is a measure of how dependent two parts of your code are on eachother.
  - High coupling: function that accesses data that is deep in the structure of an object. Requires a lot of adjustments.
  - Low coupling: minimal dependency and little changes required.
  - Solution for high coupling: only provide the data that is needed in the funciton, not the entire object. Or move function to object since it is so tightly related to the data in the object. 

## Dependency inversion

- Dependency inversion is a principe to write code that you can reaure more easily
- It's part of a group of design prinicpes that is called the SOLID principles. D stands for dependency ivnerison. 
- You want to apply an abstraction mechanism and types in your code. Python does not support this by default, but you can make use of the module called ABC (Abstract Base Class) and type hinting. 

## Links

- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
- [Python logging basics](https://www.loggly.com/ultimate-guide/python-logging-basics/)

## Formatted strings

```python
print(f"{richestDuck} has a net worth of ${netWorth}.")
>>> Scrooge McDuck has a net worth of $52348493767.5.
```

## Type hinting

You must list all your required arguments (those WITHOUT default values) before your optional arguments (those WITH default values).

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

## Precise type hinting with Enums

```python
from dataclasses import dataclass
from enum import enum

class OrgRole(Enum):
    CEO = "ceo"
    PRESIDENT = "president"
    STAFF = "staff"

@dataclass Employee:
    name:str
    role: OrgRole
```
