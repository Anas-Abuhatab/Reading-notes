# Pandas

## 10 minutes to pandas

- Importing Pandas:
```
import pandas as pd
```
- Creating a series:
```
s = pd.Series([1, 3, 5, np.nan, 6, 8])

In [4]: s
Out[4]: 
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```
- df.head() and df.tail() allow you to view the tops and bottoms, respectively, of the dataframe. 
- NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. 
- You can use booleans to filter the data that you receive. 
- Setting values by label:
```
df.at[dates[0], "A"] = 0
```
- Setting values by position:
```
df.iat[0, 1] = 0
```
- pandas primarily uses the value np.nan to represent missing data.
- To drop any rows that have missing data:
```
df1.dropna(how="any") 
                   A         B         C  D    F    E
2013-01-02  1.212112 -0.173215  0.119209  5  1.0  1.0
```
- Operations in general exclude missing data.
- You can even do operations on strings, like: s.str.lower()
- Group by:
  1. Splitting the data into groups based on some criteria
  2. Applying a function to each group independently
  3. Combining the results into a data structure
- The stack() method “compresses” a level in the DataFrame’s columns.
- Import matplotlib API:
```
import matplotlib.pyplot as plt
```
- Writing to a csv file.
```
df.to_csv("foo.csv")
```
- Reading from a csv file.
```
pd.read_csv("foo.csv")
```
- Writing to an excel file.
```
df.to_excel("foo.xlsx", sheet_name="Sheet1")
```
- Note: Page has been bookmarked for future reference. 
