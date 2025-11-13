### The EDA Process

As we have learned earlier, the focus of the EDA process is to explore the data using numerical summaries and visualizations and to identify potential relationships between variables.

The specific steps you would take in this process depend on each data set. But in general, you should:

- Find out more about the data using descriptive statistics. Descriptive statistics gives a way of giving a brief overview of the dataset we are dealing with, including some measures and features of the sample
- Consider grouping data (basic grouping with _group by_)
- Consider plotting data columns to find out how the data in the columns are distributed
- Consider creating scatter plots to explore the relationships between two numerical columns
- Conduct a hypothesis test against a hypothesis based on your understanding or observation of the data
- Consider exploring correlations among different variables (different columns)

It is worth mentioning that the EDA process invariably includes tasks to clean and transform the data. The combination of cleaning and transforming data is known as data wrangling.

### Data Wrangling in Python

The Pandas framework of Python is used to execute the steps involved in data wrangling; steps such as sorting, filtering and grouping data.

Data wrangling in Python deals with the below functionalities:

1. **Data exploration:** In this process, the data is studied, analyzed and understood by visualizing representations of data.
2. **Dealing with missing values:** Most datasets have a vast amount of missing values, _NaN_, that need to be taken care of by replacing them with mean, or mode, or simply by dropping the row with a _NaN_ value.
3. **Reshaping data:** In this process, data is manipulated according to the requirements, where new data can be added or pre-existing data can be modified.
4. **Filtering data:** Sometimes datasets are comprised of unwanted rows or columns which need to be removed or filtered
5. **Other:** By this point, you should have an efficient dataset that can be used for a required purpose like data analysis, machine learning, data visualization, model training etc.

Instruction

Read through and save this [Data Wrangling with Pandas Cheat Sheet](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf) to familiarize yourself with the Pandas functions you will use in the data wrangling process.