# Pythonisms

### Dunder Methods
- Dunder methods are predefined methods to enrich classes. 
- Start and end with double underscores. 
- Example of length dunder:
```
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```
- __getitem__ method: allows you to use Python’s list slicing syntax: obj[start:stop]
- Example of init:
```
def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
```
- __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.
- __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.
- Example of using these:
```
class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```
- Examples using __len__ and __getitem__:
```
class Account:
    # ... (see above)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]
```
- Example of using functools.total decorator (to not have to implement all of the comparison dunders) and __eq__ and __lt__:
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
- Example of using __add__:
```
def __add__(self, other):
    owner = '{}&{}'.format(self.owner, other.owner)
    start_amount = self.amount + other.amount
    acc = Account(owner, start_amount)
    for t in list(self) + list(other):
        acc.add_transaction(t)
    return acc
```
- __Call__: make your python object callable. 
- Example of an __enter__ and __exit__ dunders:
```
class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK')
```



### Iterators
- __iter__ and __next__ are the key to making a Python object iterable.
- iterators provide a common interface that allows you to process every element of a container while being completely isolated from the container’s internal structure.
- Example of manually emulating how the loop uses itertor protocol:
```
>>> repeater = Repeater('Hello')
>>> iterator = iter(repeater)
>>> next(iterator)
'Hello'
>>> next(iterator)
'Hello'
>>> next(iterator)
'Hello'
...
```
- Itertor example:
```
>>> my_list = [1, 2, 3]
>>> iterator = iter(my_list)

>>> next(iterator)
1
>>> next(iterator)
2
>>> next(iterator)
3
```


### Generators

- Example of a simple generator:
```
def repeater(value):
    while True:
        yield value
```
- calling a generator function doesn’t even run the function. It merely creates and returns a generator object:
```
>>> repeater('Hey')
<generator object repeater at 0x107bcdbf8>
```
- when a return statement is invoked inside a function, it permanently passes control back to the caller of the function.
- When a yield is invoked, it also passes control back to the caller of the function—but it only does so temporarily.
- A more in-depth example of a generator:
```
def bounded_repeater(value, max_repeats):
    count = 0
    while True:
        if count >= max_repeats:
            return
        count += 1
        yield value
```
- ^ simplified version of the above example (note that Python adds an implicit return None statement at the end of every function:
```
def bounded_repeater(value, max_repeats):
    for i in range(max_repeats):
        yield value
```