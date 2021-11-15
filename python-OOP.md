# Python - OOP

```python
class Deck:
    ranks = '23456789TJQKA'
    suits = '♠♥♦♣'
    
    def __init__(self):
        self.cards = [
            Card(rank, suit)
            for suit in self.suits
            for rank in self.ranks
        ]

deck = Deck()
print(deck.ranks)
```

### Instance variables

Instance variables (member variables) should be declared inside 
`__init__(self)` first. We don't declare them outside of the constructor.

```python
def __init__(self):
    pass
```

Underscore before variable name: precede a member variable or a method 
name with an underscore (`_`) to tell developers they shouldn't mess with it.

## Types of methods

### Class methods
Class methods must take `cls` as their first argument, and have the decorator 
`@classmethod` on the line just above the function definition. They can access 
class variables, but not instance variables.

```python
@classmethod
def make_sound(cls):
    print(cls.sound)
```

### Static methods

Static methods are similar to class methods, except they don't take `cls` as 
their first argument, and are preceded by the decorator `@staticmethod`. 
They cannot access any class or instance variables or functions. They don't
even know they're part of a class.

```python
@staticmethod
def beep():
    print("Beep boop beep")
```

### Properties

You can make any method into a property (it looks like a member variable) by putting the decorator `@property` on the line above its declaration. This can also be used to create getters.

```python
@property
def engine_strain(self):
        if not self.engines:
            return 0
        elif self.shields:
            # Imagine shields double the engine strain
            return self.engine_speed * 2
        # Otherwise, the engine strain is the same as the speed
        return self.engine_speed
```

## Class inheritance

```python
class USSDiscovery(Starship):

    def __init__(self):
        super().__init__()
        self.spore_drive = True
        self._captain = "Gabriel Lorca"
```
