# FileIO & Exceptions

## Read & Write Files in Python
- File: contiguous set of bytes used to store data.
- Files are composed of three main parts:
  1. Header: metadata about the contents of the file (file name, size, type, and so on)
  2. Data: contents of the file as written by the creator or editor
  3. End of file (EOF): special character that indicates the end of the file
File paths are broken into three major parts:
  1. Folder Path: the file folder location on the file system where subsequent folders are separated by a forward slash / (Unix) or backslash \ (Windows)
  2. File Name: the actual name of the file
  3. Extension: the end of the file path pre-pended with a period (.) used to indicate the file type
- Encoding: translation from byte data to human readable characters.
- ASCII and Unicode share the same numerical to character values. 
- Use open() to open a file before working with it. It's argument is the path to the file. 
- ALWAYS make sure an open file is properly closed. 
- Example of closing a file using the try-finally block:
```
reader = open('dog_breeds.txt')
try:
    # Further file processing goes here
finally:
    reader.close()
```
- Example of closing a file using the with statement:
```
with open('dog_breeds.txt') as reader:
    # Further file processing goes here
```
- ^ with statement automatically takes care of closing the file once it leaves the with block, even in cases of error.
- ^^ after the file name in the with statement, you can add a mode argument (such as 'r' which specieis that the file should be in read-only mode (this is default). 
- [click here for the full list of other mode options](https://docs.python.org/3/library/functions.html#open)
- A file object is "an object exposing a file-oriented API (with methods such as read() or write()) to an underlying resource."
- Three different categories of file objects:
  1. Text files
  2. Buffed binary files
  3. Raw binary files
- Read methods:
  1. .read(size=-1): reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.
  2. .readline(size=-1): reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.
  3. .readlines(): This reads the remaining lines from the file object and returns them as a list.
- You can use list() as well to create a list out of the file object. 
- Example of iterating through lines of text:
```
>>> with open('dog_breeds.txt', 'r') as reader:
>>>     # Read and print the entire file line by line
>>>     line = reader.readline()
>>>     while line != '':  # The EOF char is an empty string
>>>         print(line, end='')
>>>         line = reader.readline()
```
- Further simplied version:
```
>>> with open('dog_breeds.txt', 'r') as reader:
>>>     # Read and print the entire file line by line
>>>     for line in reader:
>>>         print(line, end='')
```
#### NOTE: The end='' is to prevent Python from adding an additional newline to the text that is being printed and only print what is being read from the file.
- Methods for writing to files:
  1. .write(string):	This writes the string to the file.
  2. .writelines(seq):	This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).
- Example using write methods:
```
with open('dog_breeds.txt', 'r') as reader:
    # Note: readlines doesn't trim the line endings
    dog_breeds = reader.readlines()

with open('dog_breeds_reversed.txt', 'w') as writer:
    # Alternatively you could use
    # writer.writelines(reversed(dog_breeds))

    # Write the dog breeds to the file in reversed order
    for breed in reversed(dog_breeds):
        writer.write(breed)
```
- Example workin with bytes:
```
>>> with open('dog_breeds.txt', 'rb') as reader:
>>>     print(reader.readline())
b'Pug\n'
```
- Example of reading a file and writing to another all at the same time:
```
d_path = 'dog_breeds.txt'
d_r_path = 'dog_breeds_reversed.txt'
with open(d_path, 'r') as reader, open(d_r_path, 'w') as writer:
    dog_breeds = reader.readlines()
    writer.writelines(reversed(dog_breeds))
```

## Exceptions in Python
- Example of a syntax error:
```
>>> print( 0 / 0 ))
  File "<stdin>", line 1
    print( 0 / 0 ))
                  ^
SyntaxError: invalid syntax
```
- Example of syntax error:
```
>>> print( 0 / 0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero
```
- Example of raising an exception:
```
x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
```
- Example (asserted that the code will be executed on a Linux system:)
```
import sys

assert ('linux' in sys.platform), "This code runs on Linux only."
```
- Try and except example:
```
try:
    linux_interaction()
except:
    pass
```
- Another example of using exception:
```
try:
    with open('file.log') as file:
        read_data = file.read()
except:
    print('Could not open file.log')
```
- Example using built-in exception FileNotFoundError:
```
try:
    with open('file.log') as file:
        read_data = file.read()
except FileNotFoundError as fnf_error:
    print(fnf_error)
```
- Breadown:
  1. try: run this code
  2. except: execute this code when there is an exception
  3. else: no exceptions? run this code.
  4. finally: always run this code. 
- Example of using the four above:
```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('Cleaning up, irrespective of any exceptions.')
```

