We will now take a look at the second phase of the ML process: **Data Preparation**. We also consider _Data Wrangling_ a part of this phase, therefore _Data Preparation_ is the part of the process that Data Scientists spend the most time on.

## What is Data Preparation

In the previous reading, we were introduced to the data pipeline and three significant stages involved in preparing data for a machine learning model. Data preparation is a part of the "Data Preprocessing" step in the established data pipeline.

Data Preparation can be split into the following parts:

1. Data Exploration:
    - Explore data
    - Explore the target variable (if we have one)
2. Find relationships between target and other variables
3. Data cleaning
    - Missing values
    - Outlier detection

### Importance of Preparing Data

If we build a website and include a broken link, it is easy to find out what’s wrong. But if we perform a wrong calculation that still provides a result, how do we know?

Beginning Data Preparation: - Get to know your data - always explore it first. - Cross-reference (more sources/tables/summarization). - Question yourself before questioning the validity of data. - Machine learning is not all-powerful, it only reflects patterns in data. We can help it with our knowledge, so that it doesn’t need to learn a probabilistic representation of what we already know.

Data preparation process can vary depending on the specific dataset and the machine learning problem being solved. However, a general framework for data preparation can include the following steps:

1. Data Understanding: Familiarize yourself with the data by reviewing the structure, size, and content. This can be done by using visualizations and summary statistics.
2. Data Cleaning: Handle missing, duplicate or inconsistent values, and remove irrelevant data. This is an important step to ensure the quality of the data being used.
3. Data Transformation: Convert the data into a format suitable for analysis and modeling. This can include normalizing, scaling, and encoding variables.
4. Data Reduction: Reduce the size of the data, if necessary, by removing features that are redundant or irrelevant to the problem.
5. Data Splitting: Split the data into training and testing datasets. The training dataset is used to build the model, while the testing dataset is used to evaluate its performance.

Once these steps are completed, the data is ready to be used for machine learning. Note that the order and specific steps may vary based on the problem and data being analyzed.

Instruction

The article [**8 Best Practices in Data Preparation**](https://www.dummies.com/article/technology/information-technology/data-science/big-data/8-best-practices-in-data-preparation-141242/) will tell us more about data prep and how to do it efficiently.