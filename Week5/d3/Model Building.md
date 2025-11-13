## Model Building

In this activity, we are going to apply everything we have learned so far to solve a complex challenge using our Python, Pandas, and statistical modelling skills.

The challenge is focused on the following topics:

- Native Python data types such as string, numbers, lists and dictionaries
- Working with JSON
- Data Exploration and transformation using Pandas
- Building statistical models such as regression and classification

### Step 1: Download JSON Files

Download [these JSON files](https://drive.google.com/file/d/1H743YlnjsPXrobVFQ5nUiSbFwoxCU2qD/view).

### Step 2: Exploring the Data

Load a couple of JSON files (you can choose the stock you want to work with) into **Pandas** and create a **DataFrame** with the following columns:

- stock acronym
- day (should be extracted from **timestamp value** in the data)
- open - price when the trading opened that day
- high - the highest price of the day
- close - price when the trading closed that day
- low - the lowest price of the day
- splits - number of splits of the stock (**look for the value splits in the events key of the JSON**).
- volume - what was the value of shares traded on that day

### Step 3: Analyze the Stock Prices, and Answer the Following Question:

- Which stock has the biggest return in 2021?
- which stock has the smallest return in 2021? (can be negative)
- Which stock had the highest number of splits?
- What was the biggest increase (%) of stock price during one day for the year 2021?

### Step 4: Build a Regression Model

Build a linear regression model that will predict the price of a stock based on another stock’s prices. You are free to choose the independent stock ticker and dependent stock ticker based on your data exploration.

### Step 5: Build a Classification Model

Can you think of a way to turn the regression problem you identified in Step 4 into a classification problem? Build a classification model based on how you rephrased your question.