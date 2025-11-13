## Performing EDA

In this activity, you will be putting together everything we have learned so far about EDA.

[This resource by nbviewer](https://nbviewer.org/github/Tanu-N-Prabhu/Python/blob/master/Exploratory_data_Analysis.ipynb) is a great example of how you would perform your exploratory data analysis (EDA). Take some time to review it before jumping into the steps below.

### Step 1: Download the Data

Download [this zipped folder](https://drive.google.com/file/d/1H743YlnjsPXrobVFQ5nUiSbFwoxCU2qD/view?usp=sharing), which contains a collection of JSON files.

### Step 2: Load the Data Files

As you may have noticed, the JSON files have a lot of information. What we decide to include in our dataframe should be informed by the questions we want to answer.

Consider all the companies listed on the NASDAQ in the folder for the year 2020. We are interested in finding out answers to the following questions:

- How much stock do we have?
- Which stock has the highest price and when it was observed?
- Which stock has the lowest price and when it was observed?
- Which stock is the most popular in 2021? (has the highest traded volume in 2021)

Now, we have to pick a single stock to act as our prototype.

Load the JSON files for the stock of your choice, write code to parse the file, and transform it into a Pandas DataFrame with the following columns:

- stock acronym
- day (should be extracted from timestamp value in the data)
- open - price when the trading opened that day
- high - the highest price of the day
- close - price when the trading closed that day
- low - the lowest price of the day
- splits - number of splits of the stock (look for the value splits in the events key of the JSON file).
- volume - what was the value of shares traded on that day

These columns will help us answer the questions above.

### Step 3: Complete the Tasks Below

#### Task 1

Once you are comfortable with your prototype code, put the code into a function. Use the function to fill out the columns in the dataframe for all companies listed on the NASDAQ in 2020.

Note

Keep in mind that while you are writing the function, you might encounter errors or exceptions that you haven’t encountered during the prototyping process. This is very common, and you will need to write code that can handle these exceptions.

#### Task 2

Now, it’s time to do some EDA. Answer the following questions.

- How big is the DataFrame (shape)?
- How much stock do we have?
- Which stock has the highest price and when it was observed?
- Which stock has the lowest price and when it was observed?
- Which stock is the most popular in 2021? (has the highest traded volume in 2021)

#### Task 3

What else could you answer by doing EDA for this dataset?

---