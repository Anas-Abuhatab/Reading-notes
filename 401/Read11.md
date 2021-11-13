# Data Analysis

## What is Jupyter Lab
- JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner.  


**About the video:**
- Gave a great introduction for what JupyterLab can do and what it supports.
- For example, you can execute live markdown and Python code. 

## Numpy Tutorial
- NumPy is a commonly used Python data analysis package.
- Data in ssv (semicolon separated values) format:
```
"fixed acidity";"volatile acidity";"citric acid";"residual sugar";"chlorides";"free sulfur dioxide";"total sulfur dioxide";"density";"pH";"sulphates";"alcohol";"quality"
7.4;0.7;0;1.9;0.076;11;34;0.9978;3.51;0.56;9.4;5
7.8;0.88;0;2.6;0.098;25;67;0.9968;3.2;0.68;9.8;5
```
- find the average quality of the wines:
```
qualities =
[float(item[-1]) for item in wines[1:]]
sum(qualities) / len(qualities)
5.6360225140712945
```
- The above code is doing:
  1. Extract the last element from each row after the header row.
  2. Convert each extracted element to a float.
  3. Assign all the extracted elements to the list qualities.
  4. Divide the sum of all the elements in qualities by the total number of elements in qualities to the get the mean.
-  A 2-dimensional array is also known as a matrix. 
- In a NumPy array, the number of dimensions is called the rank, and each dimension is called an axis. 
- We can create a NumPy array using the numpy.array function.
- One of the limitations of NumPy is that all the elements in an array have to be of the same type
- In the below example: Import the numpy package, pass the list of lists wines into the array function (converting it into a NumPy array), exclude the header row with list slicing, specify the keyword argument dtype to make sure each element is converted to a float:
```
import csv
with open("winequality-red.csv", 'r') as f:
    wines = list(csv.reader(f, delimiter=";"))
import numpy as np
wines = np.array(wines[1:], dtype=np.float)
```
- We can check the number of rows and columns in our data using the shape property of NumPy arrays:
```
wines.shape
(1599, 12)
```
- Create an array with 3 rows and 4 columns, where every element is 0, using numpy.zeros:
```
import numpy as np
empty_array = np.zeros((3,4)) 
```
- Create an array where each element is a random number using numpy.random.rand:
```
np.random.rand(3,4)
array([[ 0.2247223 , 0.92240549, 0.14541893, 0.61731257],
[ 0.00154957, 0.82342197, 0.74044906, 0.11466845],
[ 0.6152478 , 0.14433138, 0.13009583, 0.22981301]])
```
- You can find the data type of a NumPy array by accessing the dtype property:
```
wines.dtype
dtype('float64')
```
- Important NumPy data types:
```
float — numeric floating point data.
int — integer data.
string — character data.
object — Python objects.
```
- You can use the numpy.ndarray.astype method to convert an array to a different type.
- For instance, we can convert wines to the int data type:
```
wines.astype(int)
array([[ 7, 0, 0, ..., 0, 9, 5],
[ 7, 0, 0, ..., 0, 9, 5],
[ 7, 0, 0, ..., 0, 9, 5],
...,
[ 6, 0, 0, ..., 0, 11, 6],
[ 5, 0, 0, ..., 0, 10, 5],
[ 6, 0, 0, ..., 0, 11, 6]])
```
- several Python data types, including float, int, and string, can be used with NumPy, and are automatically converted to NumPy data types.
- This finds the sum of all the elements in an array by default:
```
wines[:,11].sum()
9012.0
```
- several other methods that behave like the sum method, including:
```
numpy.ndarray.mean — finds the mean of an array.
numpy.ndarray.std — finds the standard deviation of an array.
numpy.ndarray.min — finds the minimum value in an array.
numpy.ndarray.max — finds the maximum value in an array.
```
- see which wines have a quality rating higher than 5, we can do this:
```
wines[:,11] > 5
array([False, False, False, ..., True, False, True], dtype=bool)
```
- flip the axes, so rows become columns, and vice versa. We can accomplish this with the numpy.transpose function:
```
np.transpose(wines).shape
(12, 1599)
```
- numpy.ravel function to turn an array into a one-dimensional representation. It will essentially flatten an array into a long sequence of values:
```
wines.ravel()
array([ 7.4 , 0.7 , 0. , ..., 0.66, 11. , 6. ])
```