# Game of Greed 1

## How to use Random Module
- Random module allows you to generate random numbers. 
Random functions/methods:
1. Randint(): Generates a random integer by taking in a lowest and a highest number. Example:
```
import random
print random.randint(0, 5)
```
2. Random(): Generates a random number between 0 and 1. Example:
```
# Generates a random number between 0 and 100
import random
random.random() * 100
```
3. Choice(): Generates a random value from a sequence/list. Examples:
```
random.choice( ['red', 'black', 'green'] ).

---

myList = [2, 109, False, 10, "Lorem", 482, "Ipsum"]
random.choice(myList)
```
4. Shuffle(): Shuffles elements in the list, putting them in a different order. Example:
```
import random

mylist = [[i] for i in range(10)]
random.shuffle(mylist)
print(mylist)

Output:
# [[9], [2], [7], [0], [4], [5], [3], [1], [8], [6]]
# Output will very each time
```
5. Randrange(): Generates a random element from a range(start, stop, step). Example:
```
import random
# This will generate 3 random numbers between 0 and 101 with a step of 5. This is depending on the starting number. 
for i in range(3):
    print(random.randrange(0, 101, 5))
# Would output random numbers like 0, 5, 10, 15, 20, etc...

# This will generate 5 random numbers between 1 and 20 with a step of 2. 
for i in range(5):
    print(random.randrange(1, 20, 2))
# Would output random numbers like 1, 3, 5, 7 (hence never output 20).
```
Full on example:
```
import random
import itertools

# This example simulates flipping a coin 10,000 times to count how many times it comes up heads and how many times tails.

outcomes = {
    'heads': 0,
    'tails': 0,
}
sides = list(outcomes.keys())

for i in range(10000):
    outcomes[random.choice(sides)] += 1

print('Heads:', outcomes['heads'])
print('Tails:', outcomes['tails'])

# The results are tabulated in a dictionary using the outcome names as keys: 
Heads: 5091
Tails: 4909
```

## What is Risk Analysis

- The probability of any unwanted incident is defined as Risk.
- Risk analysis: Process of identifying the risks in applications or software that you built and prioritizing them to test.
- Possible risks you could encounter:
1. Use of new hardware
2. Use of new technology
3. Use of new automation tool
4. The sequence of code
5. Availability of test resources for the application
- Possible unavoidable risks:
1. he time that you allocated for testing
2. A defect leakage due to the complexity or size of the application
3. Urgency from the clients to deliver the project
4. Incomplete requirements
- Do the following things to tackle the situation with care:
1. Conduct Risk Assessment review meeting
2. Use maximum resources to work on high-risk areas
3. Create a Risk Assessment database for future use
4. Identify and notice the risk magnitude indicators: high, medium, low.
- High: means the effect of the risk would be very high and non-tolerable. The company might face loss.
- Medium: it is tolerable but not desirable. The company may suffer financially but there is a limited risk.
- Low: it is tolerable. There lies little or no external exposure or no financial loss.
- When identifying risks, there are different sets of risks:
1. Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.
2. Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.
3. Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required
4. Software Risks: You should be well versed with the risks associated with the software development process.
- Three perspectives of Risk Assessment:
1. Effect: To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.
2. Cause: To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.
3. Likelihood: To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.
- How to perform Risk Analysis:
1. Searching the risk
2. Analyzing the impact of each individual risk
3. Measures for the risk identified

## Big O Notation
- Constand time beats linear IF data is sufficiently big!
- Constany time: O(1) - think of the bird example
- Linear time: O(N) - Where n = amount of data. The amount of time it takes is dependent on the amount of data. 
- Big O is basically how time scales with respect to some input variables. 
