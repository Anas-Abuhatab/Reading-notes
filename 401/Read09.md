# Game of Greed 4 

## Dunder Methods
- In Python, special methods are a set of predefined methods you can use to enrich your classes.
- Dunder methods let you emulate the behavior of built-in types.
- Object Initialization: __init__ -----> Example:
```
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
```
- Create new accounts like this: 
```
>>> acc = Account('bob')  # default amount = 0
>>> acc = Account('bob', 10)
```
- __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.
- __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.
- Example:
```
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```
- Example querys: 
```
>>> str(acc)
'Account of bob with starting amount: 10'

>>> print(acc)
"Account of bob with starting amount: 10"

>>> repr(acc)
"Account('bob', 10)"
```
- Simple method to add transactions:
```
def add_transaction(self, amount):
    if not isinstance(amount, int):
        raise ValueError('please use int for amount')
    self._transactions.append(amount)
```
- Example of adding a property:
```
@property
def balance(self):
    return self.amount + sum(self._transactions)
```
- Make the class iterable:
```
class Account:
    # ... (see above)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]
```
- To iterate over transactions in reversed order you can implement the __reversed__ special method:
```
def __reversed__(self):
    return self[::-1]

>>> list(reversed(acc))
[30, -20, 50, -10, 20]
```
- To not have to implement all of the comparison dunder methods, I use the functools.total_ordering decorator which allows me to take a shortcut, only implementing __eq__ and __lt__:
```
from functools import total_ordering

@total_ordering
class Account:
    # ... (see above)

    def __eq__(self, other):
        return self.balance == other.balance

    def __lt__(self, other):
        return self.balance < other.balance
```

