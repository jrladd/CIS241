---
title: "Exploratory Data Analysis"
subtitle: "CIS 241, Dr. Ladd"
author: "`spacebar` to go to the next slide, `esc`/menu to navigate"
format:
  revealjs:
    theme: moon
    controls: true
    slide-level: 2
    transition: slide
    incremental: true
    center: true
    navigation-mode: vertical
    embed-resources: true
    self-contained-math: true
---

# *Look* at the Data

## John Tukey (1962)

![John Tukey pioneered Exploratory Data Analysis starting in 1962 and again with a book in 1977.](img/tukey.png)

# Summary Statistics

## Summary Statistics are focused on the **location**, **variability**, and **distribution** of data.

# Location: What is the data's "typical value"?

## Let's imagine a variable showing the heights of different dogs.

![The dog's heights (in mm) are: 600, 470, 170, 430, and 300](img/dogs1.gif)

## Mean is the sum of all values divided by the number of values.

AKA "average"

![](img/dogs2.gif)

$\dfrac{600+470+170+430+300}{5} = 394$

## We can calculate the mean easily in Python.

```python
# Put the dog heights into a dataframe
dogs = pd.DataFrame({"height": [600, 470, 170, 430, 300]})

dogs.height.mean() # Calculate the mean
```

## Median is the value such that half of the data lies above and below.

AKA "50th percentile"

![600, 470, 170, 430, 300](img/dogs1.gif)

```python
dogs.height.median()
```

## Percentile is a value such that *P* percent of the data lies below.

AKA "quantile"

## The 25th Percentile is the 1st Quartile.

![600, 470, 170, 430, 300](img/dogs1.gif)

```python
dogs.describe()
```

## The 75th Percentile is the 3rd Quartile.

![600, 470, 170, 430, 300](img/dogs1.gif)

```python
dogs.describe()
```

## The median is the 2nd Quartile!!

## An **outlier** is a data value that's different from most of the data.

AKA "extreme value"

## A **robust** variable is not sensitive to extreme values.

# Variability: Is the data tightly clustered or spread out?

## The **interquartile range** is the difference between the 1st and 3rd quartiles.

```python
dogs.height.quantile(.75)-dogs.height.quantile(.25)
```

## A **deviation** is the difference between an actual value and an estimate of location (like the mean).

![](img/dogs3.gif)

## The **variance** is the sum of the squared deviations, divided by the number of values.

![](img/dogs3.gif)

$\dfrac{206^2+76^2+(-224)^2+36^2+(-94)^2}{5} = 21,704$

## The **standard deviation** is the square root of the variance.

![It gives us a "standard" way of knowing what is normal, or what is extra large/extra small.](img/dogs4.gif)

- Rottweilers *are* tall, and dachsunds *are* short---compared to the standard deviation from the mean.
- Outliers are often more than two standard deviations from the mean.

## Now calculate the variance and standard deviations in Python.

```python
dogs.height.var()

dogs.height.std()
```

Were these the results you expected?

## Population vs. Sample

- Population: the full data that exists (i.e. all the dogs in the world)
- Sample: the actual data that was collected (i.e. our set of 5 dogs)

## Population vs. Sample

When you have "N" data values:

- The Entire Population: divide by N when calculating variance (like we did)
- A Sample: divide by N-1 when calculating variance

- Sample variance: $\dfrac{108,520}{4}=27,130$  
- Sample standard deviation: $\sqrt{27,130}=164$

- Think of it as a "correction" when your data is only a sample. Pandas does this by default!

## Neither the mean, variance, nor standard deviation are **robust**. They are all very sensitive to outliers!

# Distributions: How many of each value are there?

## Histograms show distributions based on frequency counts.

![The histogram for miles per gallon highway in the mpg dataset.](img/mpg_hwy_hist.png)

## The normal distribution has most values in the middle.

![In a normal distribution, 95% of the values lie within 2 standard deviations of the mean.](img/normal.png)

Be careful: normal distributions are assumed for many statistical analyses!

## Boxplots show distribution based on the median.

![You can see how the box plot and the histogram are similar but different.](img/eda-boxplot.png)

# Correlation: Are two variables related?

## Location, Variability, and Distribution are for one variable at a time (univariate analysis). Correlation is for *two* variables (bivariate analysis).

## Scatter plots and correlation coefficients are used to determine correlation.

We'll talk more about correlation in a couple weeks!

# Resampling and Confidence Intervals

## Resampling is simply drawing multiple random samples from observed data.

I can grab a sample of 5 observations. Then I can "resample" 5 more. Then 5 more, and so on and so on.

## First proposed in the 1960s, resampling procedures weren't practical until computing took off in the 1980s.

## Resampling is an umbrella term. It can include:

- The Bootstrap, used to assess the reliability of an estimated statistic
- Permutation Tests, used as an alternative to parametric hypothesis tests

## You can resample with or without *replacement*.

Replacement means an item is returned to the sample before the next draw (i.e. you could wind up with the same observation multiple times).

## Using bootstrap sampling, we can estimate a confidence interval for any summary statistic.

- Remember: bootstrap sampling is sampling *with* replacement.
- The 90% confidence interval tells us where 90% of the data is likely to fall, if the data were random.
- Confidence intervals are used to gauge *uncertainty*. 

## Confidence intervals with Pandas

<small>Work with a partner to calculate the confidence interval for the mean height in the `dogs` dataframe (remember to use your Pandas cheatsheet and past slideshows):

1. Find the number of rows in the dataframe, assign to a variable `n_rows`.
2. Create a `for` loop through a list of 5000 numbers using `range(5000)`.
    a. In the loop, use the [`sample()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sample.html#pandas.DataFrame.sample) function where `n=` your number of rows and `replace=True`.
    b. Get the `mean()` of the height column of each sample, and assign it to a variable.
    c. Use `append()` to add your sample means to an empty list.
3. Turn the list in to a Pandas Series with `pd.Series(your_list)`.
4. Find the 95th percentile (quantile) and the 5th percentile (quantile) and assign each to a variable.
5. `print()` your results using [f-strings](https://www.geeksforgeeks.org/formatted-string-literals-f-strings-python/).
    a. The result should read: "The mean dog height in our data is \_\_\_\_\_\_\_, with a 90% confidence interval of \_\_\_\_\_ to \_\_\_\_\_."

</small>

## Confidence intervals with Pandas

```{.python code-line-numbers="|1|6|7|5,8|11|14,15|18|"}
n_rows = dogs.shape[0] # First find the number of rows in the dataframe.

# Then take a sample with replacement from your dataset, and
# Calculate the mean each time. Do this 5000 times.
bootstrap_samples = []
for i in range(5000):
    sample_mean = dogs.sample(n=n_rows, replace=True).height.mean()
    bootstrap_samples.append(sample_mean)

# Put the results into a pandas Series object
bootstrap_samples = pd.Series(bootstrap_samples)

# Calculate the 95th percentile and the 5th percentile.
top_percentile = bootstrap_samples.quantile(.95)
bottom_percentile = bootstrap_samples.quantile(.05)

# Print the results using nice f-strings.
print(f"The mean dog height in our data is {dogs.height.mean():.3f}, with a 90% confidence interval of {bottom_percentile:.3f} to {top_percentile:.3f}.")
```
