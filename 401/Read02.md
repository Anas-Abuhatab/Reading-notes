# Testing and Modules

## In Tests We Trust - TDD with Python
### Unit tests and TDD?
- TDD: Test-Driven Development
- Unit tests: Pieces of code to exercise the input/output and code behavior.
- Tdd is a startegy to think and write tests first.

#### the freela 
- Example of using Genderize.io API to identify gender of potential leads:
```
requests.get('https://api.genderize.io/?name=ana')
```
#### Important aspects about the unit test
- First test example:
```
def test_should_return_female_when_the_name_is_from_female_gender():
    detector = GenderDetector()
    expected_gender = detector.run(‘Ana’)
    assert expected_gender == ‘female’
```
- It is ideal to separate test folder from production code. For example:
```
mymodule/
 — module.py
 — another_folder/
 — — another_module.py
tests/
 — test_module.py
 — another_folder/
 — — test_another_module.py
```
- AAA: Arrange, Act and Assert.
1. Arrage: organize data needed to execute that piece of code (input)
2. Act: execute code being tested
3. Assert: after execution, check if result (output) is what was expected.

### The Cycle
- The cycle is made up of 3 steps:
1. Write unit test and make it fail
2. Write the feature and make test pass
3. Refactor the code 

#### TDD is not about the money/tests
- Example of test for male name:
```
def test_should_return_male_when_the_name_is_from_male_gender():
    detector = GenderDetector()
    expected_gender = detector.run(‘Pedro’)
    assert expected_gender == ‘male’
```
- Real code for the example:
```
import requests

def run(self, name):
    result = requests.get('https://api.genderize.io/?name{}'
.format(name))
    return result['gender']
```
### Recursion
- Recursion is the process of a function calling itself directly or indirectly. 
- base condition: solution to base case is provided and the solution of bigger problem is expressed in terms of the smaller problems:
```
int fact(int n)
{
    if (n < = 1) // base case
        return 1;
    else    
        return n*fact(n-1);    
}
```
- If the bace case is never reached ,it may cause a stack overflow
- A recursive function is tail recursive when the recursive call is the last thing executed by the function.
- disadvantages of recursive over iterative: greater space requirements since all functions remain in stack until base case is reached.
- disadvantages of iterative over recursive: recursive is clean and simple. Some problems are inheretly recursive.

