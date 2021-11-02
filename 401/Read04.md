# Classes, Objects, Pytest, and Thinking Recursively

## Classes and Objects
- "Objects are an encapsulation of variables and functions into a single entity. Objects get their variables and functions from classes. Classes are essentially a template to create your objects."
- Example of creating a new object (myobjectx) using the MyClass class:
```
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()
```
- ^ myobjectx can now access the variables and functions from the class that was used to create it (MyClass). 
- Example:
  1. We have a class defined for vehicles. Create two new vehicles called car1 and car2. Set car1 to be a red convertible worth $60,000.00 with a name of Fer, and car2 to be a blue van named Jump worth $10,000.00.
```
# define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# your code goes here
car1 = Vehicle()
car1.name = "Fer"
car1.color = "red"
car1.kind = "convertible"
car1.value = 60000.00

car2 = Vehicle()
car2.name = "Jump"
car2.color = "blue"
car2.kind = "van"
car2.value = 10000.00

# test code
print(car1.description())
print(car2.description())
```

## Thinking Recursively
- algorithm for iterative present delivery implemented in Python:
```
houses = ["Eric's house", "Kenny's house", "Kyle's house", "Stan's house"]

def deliver_presents_iteratively():
    for house in houses:
        print("Delivering presents to", house)
```
- algorithm for recursive present delivery implemented in Python:
```
houses = ["Eric's house", "Kenny's house", "Kyle's house", "Stan's house"]

# Each function call represents an elf doing his work 
def deliver_presents_recursively(houses):
    # Worker elf doing his work
    if len(houses) == 1:
        house = houses[0]
        print("Delivering presents to", house)

    # Manager elf doing his work
    else:
        mid = len(houses) // 2
        first_half = houses[:mid]
        second_half = houses[mid:]

        # Divides his work among two elves
        deliver_presents_recursively(first_half)
        deliver_presents_recursively(second_half)
```
- Recursive function for calculating n! implemented in Python:
```
def factorial_recursive(n):
    # Base case: 1! = 1
    if n == 1:
        return 1

    # Recursive case: n! = n * (n-1)!
    else:
        return n * factorial_recursive(n-1)
 >>> factorial_recursive(5)
120
```
- Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case. Then, the stack begins to unwind as each call returns its results.
- To maintain state during recursion you have to either:
    1. Thread the state through each recursive call so that the current state is part of the current call’s execution context
    2. Keep the state in global scope
- Example of maintaining state by threading it through each recursive call (i.e. passing the updated current state to each recursive call as arguments):
```
def sum_recursive(current_number, accumulated_sum):
    # Base case
    # Return the final state
    if current_number == 11:
        return accumulated_sum

    # Recursive case
    # Thread the state through the recursive call
    else:
        return sum_recursive(current_number + 1, accumulated_sum + current_number)
# Pass the initial state
>>> sum_recursive(1, 0)
55
```
- maintain the state by keeping it in global scope:
```
# Global mutable state
current_number = 1
accumulated_sum = 0

def sum_recursive():
    global current_number
    global accumulated_sum
    # Base case
    if current_number == 11:
        return accumulated_sum
    # Recursive case
    else:
        accumulated_sum = accumulated_sum + current_number
        current_number = current_number + 1
        return sum_recursive()
 >>> sum_recursive()
55
```
- In Python, global keyword allows you to modify the variable outside of the current scope. It is used to create a global variable and make changes to the variable in a local context.
- A data structure is recursive if it can be deﬁned in terms of a smaller version of itself.
- Recursion can also be seen as self-referential function composition. We apply a function to an argument, then pass that result on as an argument to a second application of the same function, and so on.
- List is not the only recursive data structure. Other examples include set, tree, dictionary, etc.
- calculating the sum of all the elements of a list recursively:
```
def list_sum_recursive(input_list):
    # Base case
    if input_list == []:
        return 0

    # Recursive case
    # Decompose the original problem into simpler instances of the same problem
    # by making use of the fact that the input is a recursive data structure
    # and can be deﬁned in terms of a smaller version of itself
    else:
        head = input_list[0]
        smaller_list = input_list[1:]
        return head + list_sum_recursive(smaller_list)
        
>>> list_sum_recursive([1, 2, 3])
6
```

## Pytest Fixtures and Coverage

- pytest: a library for testing Python code
#### Fixtures
- You define a fixture using the pytest.fixture decorator, along with a function definition.
Example:
```
@pytest.fixture
def simple_file():
   return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))
```
- ^ provides your test with the appropriate object at the right time.
Inside the test, you can access the fixture by name. For example:
```
def test_reverse_lines(simple_file):
   assert reverse_lines(simple_file) == ['cba\n', 'fed\n',
 ↪'ihg\n', 'lkj\n']
```
- Fixtures can make calculations and decisions, unlike regular data. Fixtures are actualyl functions under the hood.
Example of setting the scope of the fixture to be "module", so it'll be available throughout your tests but will execute only a single time:
```
@pytest.fixture(scope='module')
def simple_file():
   return StringIO('\n'.join(['abc', 'def', 'ghi', 'jkl']))
```
#### Coverage
- How do you include coverage in tests? "there's a package called pytest-cov on PyPI that you can download and install. Once that's done, you can invoke pytest with the --cov option. If you don't say anything more than that, you'll get a coverage report for every part of the Python library that your program used."
```
pytest --cov=mymul .
coverage html
```