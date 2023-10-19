Object-Oriented Programming (OOP) is a programming paradigm that revolves around the concept of "objects", which are instances of classes. In Python, classes are used to define the structure and behavior of objects.
### Creating a Class

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

In this example, we create a class called `Deck` which represents a deck of playing cards. It has class variables `ranks` and `suits` representing the ranks and suits of the cards. The `__init__` method initializes the deck by creating a list of `Card` objects.
## Instance variables

Instance variables, also known as member variables, are declared inside the `__init__(self)` method. These variables store information unique to each instance of the class.

```python
def __init__(self):
    self.cards = [] # Initialize as an empty list 
    self._top_card = None # Underscore indicates it's not meant to be accessed externally
```

The underscore before `_top_card` is a convention to suggest that this variable is intended for internal use and shouldn't be manipulated directly from outside the class.

## Types of methods

### Class methods

Class methods are associated with the class itself rather than instances of the class. They use the `@classmethod` decorator and take `cls` as their first argument.

```python
@classmethod 
def create_full_deck(cls): 
	return cls()
```

In this example, `create_full_deck` is a class method that creates a full deck of cards. It returns a new instance of the `Deck` class.

### Static Methods

Static methods don't depend on class or instance variables and are independent of the class they belong to. They use the `@staticmethod` decorator.

```python
@staticmethod
def shuffle_cards(cards):
    return random.shuffle(cards)
```

Here, `shuffle_cards` is a static method that shuffles a list of cards.

### Properties

Properties allow you to access methods like they were attributes. They are created using the `@property` decorator.

```python
@property
def top_card(self):
    return self._top_card
```

In this case, `top_card` acts like an attribute, allowing you to retrieve the value of `_top_card`.

## Class Inheritance

Inheritance is a fundamental concept in OOP that allows a class (subclass) to inherit attributes and behaviors from another class (superclass).

```python
class USSDiscovery(Starship):

    def __init__(self):
        super().__init__()
        self.spore_drive = True
        self._captain = "Gabriel Lorca"
```

In this example, `USSDiscovery` is a subclass of a hypothetical `Starship` class. It inherits attributes and methods from `Starship` and adds its own unique attributes like `spore_drive` and `_captain`.

[[python]]