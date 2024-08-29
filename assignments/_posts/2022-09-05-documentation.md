---
title:  "Documentation Assignment"
date:   2023-08-31 09:00:00 -0400
show_date: false
---
**Complete by: Thursday 12 Sept. by 10:55am**

The goal of this assignment is to get you more familiar with finding, understanding, and documenting a data set. You'll find a dataset online and create documentation and metadata for it, using the guidelines below.

## Finding a Dataset

You can choose whatever data set you want so long as it comes from a reputable source (see the links below) and it's large enough for you to write about. This should be a *rectangular dataset* with rows and columns, ideally available as a CSV or spreadsheet file. Try to find a data set that has a mix of numerical and categorical variables. **You will turn in the original data file along with your documentation.**

You can choose data from whatever topic you like. Remember that there are data sets out there from almost every area of study that you can imagine! Here are some ideas to get you started:

* **Anthropology and Sociology**
* **Biology**
* **Economics/Business**
* **Physics**
* **Political Science**
* **Psychology**
* **Philosophy**
* **Sports Analytics**
* **Arts & Humanities**

Don't just settle for the very first dataset you find: look around a bit for interesting or unexpected ones!

Later in the semester, you'll choose a dataset to work on for your final project. This assignment is unrelated, so you can decide to stick with this dataset later on or choose something completely new: it's entirely up to you.

**Mostly, choose something that you are curious about and will allow you to demonstrate the listed concepts for the assignment. *Have some fun with it!***

### Where can I find datasets?

The Data page of the [CIS LibGuide](https://libguides.washjeff.edu/cis/data) has an extensive list of data resources, including general sites as well as repositories broken down by topic.

**You *may not* choose any datasets from Kaggle or Data.world. These are general repositories that often make it more difficult to find the original collectors or purpose of the data.**

## Writing Your Documentation

Below is a suggested format to use to make sure the useful information is communicated to a reader or potential data user (you too!) needed to interpret and understand it. As you edit, remove any instructional or template text and replace with your own. If you have questions particular to your dataset or another idea for how to present the codebook and documentation, please discuss in advance with me.

---

**Dataset Name**

**Data source:** Name of data provider, website, and link

**Original data collectors:** Names of people or organization

**Data size:** e.g. number of KB or MB

**Special permissions:** Note if the data is freely available, published, or has restrictions for use.

1-2 short paragraphs describing the data table(s) you plan to use. Your description should describe what one row (observation) represents, as well as any potentially “tricky” or difficult aspects of the dataset - for example, how is missing data denoted in the dataset? If the dataset already had a well-defined codebook or metadata provided that can give additional information, please link to it here. You can also mention any potential ethical issues one should be aware of when using this data.


[*n.b. You dataset may already have some written documentation when you find it. It's okay to read that and think about it as you work, but your final paragraphs should all be in **your own words**.*]

**Name_of_your_datafile.csv**

**Data Dictionary**:

_Please note that if your data set has multiple data tables, you will need to provide more than one of these data dictionary tables, one for each dataset. You should make a note about which column in each dataset contains common information, and represents the “link” or the “key” between them._

Column Name|Variable Definition|Data Type|Units|Variable Codes and Ranges|Missing Value Codes
---|---|---|---|---|---
The name of the column, exactly as it appears in your .csv file|Describe what each variable represents, and if known, how it was measured.|if units needed; grams, days…|Say whether the data is numerical or categorical, and give a subcategory (e.g. continuous)|if not a continuous variable, you could list the acceptable values|if there is missing data, indicate what is used, e.g. blank, NA, NULL, etc.

Add more rows as needed... [n.b. *You only need to create a chart of 20 variables. If your data set has more than 20 variables, just choose the 20 that seem the most relevant or interesting.*]

For **Variable Definition**, If you don’t know or don’t have information on how to interpret a variable, or want to give a word of caution, say so here. If the variable has any special considerations or challenges inherent to its measure, you may note that here, too.

For **Variable Codes and Ranges**, If you don’t need to specify acceptable values, you can just fill this in with NA (for not applicable).

**Data Wrangling**:

Write a paragraph explaining the wrangling steps you will need to take in order to ensure that this data is **in tidy form and ready for analysis**.

This may include: selecting a subset of the data, creating new columns, renaming existing columns, sorting data, grouping and summarizing, or even splitting columns and pivoting the table. Be sure to ask me if you have questions about what wrangling steps should be taken! You may find it easiest to attempt these wrangling steps yourself, but you do not need to submit the code for this assignment. **Be specific about exactly what columns, rows, and values you should change and why.**

---

**Requirements**:

- Turn in your documentation (as a PDF) via Sakai
- Format the documentation according to the template above
- Also turn in the original data file that you found online (ideally a CSV)
