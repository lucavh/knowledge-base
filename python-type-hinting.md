By using type hints, programmers can improve code readability and catch potential errors early during development. While type hints are not enforced at runtime by the Python interpreter, they can be checked using tools like `mypy` to ensure type consistency.

```python
def add_numbers(a: int, b: int) -> int:
return a + b  

add_numbers(5, 10)  
>>> 15
```

In this example, we use type hints to specify that the function `add_numbers` takes two arguments `a` and `b`, both of type `int`, and returns an `int`. This clarifies the expected types of inputs and the return value, making it easier for other developers to understand and use the function correctly.

## Optional type hints

```python
def addPilot(name: Optional[str] = None):
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
