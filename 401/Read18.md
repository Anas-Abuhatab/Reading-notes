# Automation

### Python Regular Expressions Tutorial

- regex: sequence of characters used to check whether a pattern exists in a given text (string) or not. 
- Regex is essential for text mining.
- Import regex: 
```
import re
```
- Example of ordinary character matching:
```
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")
Match!
```
- The match() function returns a match object if the text matches the pattern. Otherwise, it returns None.
- r = raw string literal. 
- Special characters: Do not match themselves but hold special meaning. 
- A period matches any character except for newline. 
- A example using search and group:
```
re.search(r'Co.k.e', 'Cookie').group()
'Cookie'
```
- ^ matches the start of a string. Example:
```
re.search(r'^Eat', "Eat cake!").group()
'Eat'
```
- $ matches the end of a string. Example: 
```
re.search(r'cake$', "Cake! Let's eat cake").group()
'cake'
```
- [abc]: Matches a or b or c.
- [a-zA-Z0-9]: Matches any letter from (a to z) or (A to Z) or (0 to 9).
- Example:
```
re.search(r'[0-6]', 'Number: 5').group()
'5'
```
- What \ could mean:
  1. If the character following the backslash is a recognized escape character, then the special meaning of the term is taken.
  2. Else if the character following the \ is not a recognized escape character, then the \ is treated like any other character and passed through.
  3. \ can be used in front of all the metacharacters to remove their special meaning. 
- \w - Lowercase 'w'. Matches any single letter, digit, or underscore.
- \W - Uppercase 'W'. Matches any character not part of \w (lowercase w).
- \s - Lowercase 's'. Matches a single whitespace character like: space, newline, tab, return.
- \S - Uppercase 'S'. Matches any character not part of \s (lowercase s).
- \d - Lowercase d. Matches decimal digit 0-9.
- \D - Uppercase d. Matches any character that is not a decimal digit.
- Grouping example:
```
statement = 'Please contact us at: support@datacamp.com'
match = re.search(r'([\w\.-]+)@([\w\.-]+)', statement)
if statement:
  print("Email address:", match.group()) # The whole matched text
  print("Username:", match.group(1)) # The username (group 1)
  print("Host:", match.group(2)) # The host (group 2)
Email address: support@datacamp.com
Username: support
Host: datacamp.com
```
- The syntax for creating named group is: (?P<name>...)
