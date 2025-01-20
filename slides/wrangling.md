---
title: "Data Wrangling with Python & Pandas"
subtitle: "CIS 241, Dr. Ladd"
author: "Hit the spacebar to go to the next slide"
format:
  revealjs:
    theme: solarized
    controls: true
    slide-level: 2
    transition: slide
    incremental: true
    center: true
    navigation-mode: vertical
    embed-resources: true
---

# Key Resources

- [Python for Data Analysis](https://wesmckinney.com/book/) by Wes McKinney
- [Elements of Data Science](https://allendowney.github.io/ElementsOfDataScience/) by Allen B. Downey
- [Intro to Cultural Analytics & Python](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/00-Python.html) by Melanie Walsh
- [Pandas official documentation](https://pandas.pydata.org/docs/user_guide/index.html#user-guide)

*These slides don't contain everything you will need to know! Make sure to refer to the links above as well as the Pandas cheatsheet.*

# What's the Difference Between Python, Pandas, and Jupyter?

## Python is a programming *language*.

It's the code you write.

`somevariable = 5 + 6`

## Pandas is a library.

Libraries store reusable functions and methods. They need to be imported at the top of your code.

```{.python code-line-numbers="2|3|4"}
# These are our standard imports
import pandas as pd # Data analysis
import numpy as np # Numerical Calculation
import altair as alt # Visualization
```

## Jupyter is a program, an "integrated development environment" (IDE).

You can write Python in different places, but in this class we will write and run Python inside JupyterHub.

![](img/jupyter_blank.png)

## JupyterHub lets you store and access `.ipynb` files.

Files are organized in a *hierarchy* of directories, just like on your computer.

![](img/jupyter_blank.png)

# The Basics

Python and Pandas both have *syntax*, the way that you code. But the syntax for each is a little different!

## Variables store information

```{.python code-line-numbers="2|4|8"}
# In Python, anything can be stored in a variable
myvar = 5

myvar #or print(myvar)

# In Pandas, whole spreadsheets can be "read"
# and then stored in a variable
cars = pd.read_csv('https://raw.githubusercontent.com/mwaskom/seaborn-data/master/taxis.csv')
cars
```

Data in Pandas can be loaded from a filename or a URL.

Use descriptive variable names, and avoid spaces!

## You Try It!

1. Create a variable called `newVar` that is equal to the value of five plus seven. Then display your variable to see what its value is.
2. Create a variable called `penguins` to hold the data available at `https://jrladd.com/CIS241/data/penguins.csv`. Then display the DataFrame in Jupyter.

## Add frequent comments to explain what your code does.

Comments in Python begin with a `#` symbol.

```python
# This variable contains a continuous value
some_variable = 2.5
```

You should also use comments for citations!

## Variables have types, and so do Pandas columns.

- String or Character: a piece of text (ex. `"five"`)
- Integer: a discrete numerical value (ex. `5`)
- Float or Double: a continuous numerical value (ex. `5.0`)

```{.python code-line-numbers="1|3|5"}
stringvar = "five"

type(stringvar)

cars.info()
```

## You Try It!

1. Find the type of `newVar`, that you created in the last exercise. 
2. Find all the data types in the penguins dataframe.

# Manipulating Data

## Individual data types (strings, floats, integers) can be put into container data types (lists, dictionaries, series, dataframe).

## A Python list and a Pandas Series contain an ordered collection of items.


```python
# A list is surrounded by brackets and can contain any kind of data.
mylist = [5,6,7]

secondlist = ["cat","dog","fish"]

# Access items in a list
mylist[0]
secondlist[1]

# A Series is the Pandas version of a list and works the same way.
# Every column of a DataFrame is its own Series.
myseries = pd.Series(mylist)
myseries[0]
```

## A Python dictionary and a Pandas DataFrame contain key/value pairs.

```{.python code-line-numbers="1|3-5|7-11|13-15"}
mydictionary = {"pet_name": "Fido", "age": 5, "pet_type": "dog"}

# Access items in a dictionary
mydictionary["pet_name"]
mydictionary["age"]

# Every DataFrame is made up of multiple Series columns
# You access these like keys in a dictionary.

taxis["distance"] # Dictionary notation
taxis.distance # Dot notation

# Or get a whole set of columns in a new DataFrame 
prices = taxis[['fare','tip','tolls','total']]
prices
```

## You Try It!

- Create a list of 7 items of *different data types*.
  - Display the 4th item in the list.
  - Display the 2nd through 5th items.
  - Display the 3rd from last item.
- Display the 8th item in the species column of the penguins DataFrame.

## Loops and Conditions let you manipulate stored data.

## You can use the `for` operator to *iterate* through a list.

```python
mylist = [5,6,7,8]
for item in mylist:
  addone = item + 1
  print(addone)
```

## You can use `if` and `else` to set *conditions*.

```{.python code-line-numbers="|2|3|4|6|8"}
# Let's use the range() function to make a list
newlist = range(1,11) 
for i in newlist:
  if i-5 == 0:
    print("It's five!")
  elif i-5 == 5:
    print("It's ten!")
  else:
    print("Nope, try again...")
```

## Pandas combines loops and conditions by letting you filter rows based on a condition in brackets.

```python
cheap_fares = taxis[taxis.total < 10]
cheap_fares
```

Remember to save everything in variables

## Row selection uses standard comparisons.

- `>` greater than
- `>=` greater than or equal to
- `<` less than
- `<=` less than or equal to
- `!=` not equal
- `==` equal (note the double equals sign!)

## You can also use logical operators to combine comparisons.

& "and", | "or", and ! "not"

![](img/transform-logical.png)

## Logical operators can also be combined.

```python
extreme_fares = taxis[(taxis.total < 7) | (taxis.total > 50)]
extreme_fares
```

## You Try It!

- Loop through the list you created in the last exercise, and print each item one-by-one.
- Use a filter condition to create a dataframe of all the penguins in the Adelie species.

# Wrangling Data

## Why not just edit the data in the spreadsheet?

## A function is a command that runs based on some *input* or *parameter*.

Python has many built-in functions.

```python
# Some functions give a number result
sum([5,6,7])
mylist = [5,6,7]
sum(mylist)
len(mylist)

# But functions can do anything! 
type(mydictionary)
```

Functions can do just about anything: calculate values, create graphs, transform data, etc.

## You can create functions like you create variables.

```python
def get_last_value(some_list):
  return some_list[len(some_list) - 1]

get_last_value(mylist)
```

## Pandas uses both functions and methods.

```{.python code-line-numbers="1-2|4-5"}
# Functions are wrapped around a DataFrame or Series
pd.unique(myseries)

# Methods come after a DataFrame or Series
myseries.unique()
```

## The `.sort_values()` method lets you sort rows by value.

```python
taxis.sort_values("distance", ascending=False)
```

## `.rename()` lets you rename columns.

```python
taxis = taxis.rename(columns={"fare": "base_fare"})
taxis
```

Notice we kept the same variable name here!

## `.assign()` lets you add new columns based on existing ones.

```python
taxis_new_column = taxis.assign(total_per_person = taxis.total/taxis.passengers)
taxis_new_column
```

## You try it!

Sort the penguins dataframe by flipper length, with the shortest flippers at the top.

# Grouping and Summarizing

## We use `.groupby()` with summary statistics to make *summary tables*.

*Summary tables* are new dataframes that summarize our original data.

This paradigm is known as *split-apply-combine*, and it's key to data analysis.

## You can use summary statistic methods to get values for a whole column.

```python
taxis["tip"].mean() # Dictionary notation
taxis.tip.mean() # Dot notation
```

Stat functions to use: `mean(), median(), min(), max(), std()`.

## Groupby lets you group data, to get summaries for each group.

```python
taxis.groupby(['dropoff_borough'])
```

It doesn't look like anything on its own!

## Now we can put it all together!

```python
# Use multiple methods to "chain" operations
taxis.groupby(["dropoff_borough"]).mean(numeric_only=True)
```

## You try it!

Create a summary table showing the average bill depth of penguins for each species.
