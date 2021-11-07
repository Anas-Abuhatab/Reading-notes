# Game of Greed 2

## Python Scope  
**Scope:**  
- Global: The names that you define in this scope are available to all your code.
- Local: The names that you define in this scope are only available or visible to the code within the scope.
- The Python scope concept is generally presented using a rule known as the LEGB rule.  

**LEGB:**  
- Stands for Local, Enclosing, Global, and Built-in. 
- Enclosing: Special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function.
- Built-in: created or loaded whenever you run a script or open an interactive session. This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python.
- Keywords can be used to change the scope of a variable.  

**Global:**  

**Trying to update a global variable from within a function:**  
```
counter = 0  # A global name
>>> def update_counter():
...     counter = counter + 1  # Fail trying to update counter
...
>>> update_counter()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in update_counter
UnboundLocalError: local variable 'counter' referenced before assignment
```
- As you can see above, this did not work. Now let's see what happens when you use the global statement:
```
>>> counter = 0  # A global name
>>> def update_counter():
...     global counter  # Declare counter as global
...     counter = counter + 1  # Successfully update the counter
...
>>> update_counter()
>>> counter
1
>>> update_counter()
>>> counter
2
>>> update_counter()
>>> counter
3
```
- As you can see, adding the global keyword allowed us to update the global scoped counter from inside the function. 
- Note: The use of global is considered bad practice in general. If you find yourself using global to fix problems like the one above, then stop and think if there is a better way to write your code. For example, you can try to write a self-contained function that relies on local names rather than on global names as follows:
```
>>> global_counter = 0  # A global name
>>> def update_counter(counter):
...     return counter + 1  # Rely on a local name
...
>>> global_counter = update_counter(global_counter)
>>> global_counter
1
>>> global_counter = update_counter(global_counter)
>>> global_counter
2
>>> global_counter = update_counter(global_counter)
>>> global_counter
3
```

**Nonlocal:**  
- The following example shows how you can use nonlocal to modify a variable defined in the enclosing or nonlocal scope:
```
>>> def func():
...     var = 100  # A nonlocal variable
...     def nested():
...         nonlocal var  # Declare var as nonlocal
...         var += 100
...
...     nested()
...     print(var)
...
>>> func()
200
```
- With the statement nonlocal var, you tell Python that you’ll be modifying var inside nested().
- You can’t use a nonlocal statement in either the global scope or in a local scope. Here’s an example:
```
>>> nonlocal my_var  # Try to use nonlocal in the global scope
  File "<stdin>", line 1
SyntaxError: nonlocal declaration not allowed at module level
>>> def func():
...     nonlocal var  # Try to use nonlocal in a local scope
...     print(var)
...
  File "<stdin>", line 2
SyntaxError: no binding for nonlocal 'var' found
```

## Don’t be CONFUSED by BIG O notation anymore!
- Big O Time: Basically how long it takes an algorithm to do things. 
- Big O Space: ^How much memory that algorithm takes while doing it.
- Why is it necessary? It is a good way to compare algorithms and determine performance/efficiency. 
- Big O is also useful for measuring how an algorithm will respond to an increasing amount of data it has to process. 
- Big O notation will always give you the worst scenerio. 
- O(1): Constant running time
- O(log n): Logarithmic running time 
- O(n): Linear running time 
- O(n logn): Log-linear running time
- O(n^k): Polynominal running time. 
- O(c^n): Exponential running time.