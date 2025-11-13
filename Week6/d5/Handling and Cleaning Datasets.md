## How to Handle and Clean Datasets for ML

Just as the first step in all good cooking recipes is to procure the right ingredients and prep them well, the first step in building an ML model begins with taking a look at the data we will feed into our model. Ideally, we have accurate and clean data right off the bat that we can feed into our ML model, but in reality, this seldom happens. We often have to start right at the beginning: collect the data we need, clean the data to remove incorrect and missing entries, and pre-process it so the data behaves well and can finally be fed into our model.

In this section, we will discuss the entirety of this ‘data preparation pipeline’ for ML and the best practices and common pitfalls.

All too often in the industry, highly compensated data scientists spend up to 80% of their time creating the data pipeline and resolving issues. Knowing how to navigate the pipeline and knowing the pitfalls can make the process time-efficient.

![The data pipeline (collection - formatting - pre-processing) is depicted.](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Data+Prep/Handling-and-Cleaning-Datasets.png)

### Data Collection

Businesses have always tended to produce enormous amounts of data of a diverse variety – right from sales or inventory data to audio files of consumer complaint calls.

As the cost of digital storage has cheapened, it has become more economically viable to store the vast and diverse data generated. The best time for companies to start collecting and storing their data was yesterday, the second best time is today.

Of course, it is challenging to know beforehand what kind of data will be helpful for future projects and therefore should be stored. And what kind of data is unnecessary to collect. Therefore, data collection has to be a strategic decision integrated across departments and has to be reassessed periodically.

It is also typically a good idea to keep the data raw without too much pre-processing at this stage. Low storage costs make this a viable proposition. This ensures we do not throw out useful information in the data before knowing what the end use of the data is going to be.

Apart from internal data, sometimes, data scientists may also need to pull in external data for their ML projects. For example, information about the pricing of competitors, customer sentiment on social media, and tweets about your products vs. competitors are all useful pieces of information that can be pulled in from external sources and stored internally.

### Data Formatting

The data, at this stage, has been gathered from various internal and external sources, and is spread across multiple tables. For example, customer complaint data from different provinces with different languages, or sales data from countries with different currencies, etc. may need to be gathered together to form an integrated data set.

If data is being aggregated from different sources, say different branches of the same company, care has to be taken to ensure that the variables in the data are being consistently coded. For example, a time variable may be coded down to the date in some data while down to the month in other datasets.

In instances where data is routinely exchanged between different organizations or different parts of the company, data standards, i.e., standardizing how data is stored, can play a huge role in enhancing interoperability and allowing data to be transferred and used seamlessly.

Another issue to keep in mind while handling time-series data is to ensure the data is formatted temporally. This will help prevent the problem of target leakage or data leakage while building models.

For example, let us suppose we are building a ML model to predict whether the Vancouver Canucks hockey team will win or lose their next game based on matches from past seasons. Then, if we use their average performance over the entire season as a feature while predicting the outcome of a game, that would be wrong

This is because the team's performance may vary significantly from game to game, and factors such as injuries, weather conditions, and the opposing team's performance may affect the outcome of a particular game.

This is why, To ensure that our ML model performs accurately, we need to ensure that the data we gather is in the appropriate format and careful data formatting at the outset of a data science or a ML project can save days or weeks of wasted effort down the line.

### Data Pre-Processing.

Data pre-processing is the last, but no less important, stage in the data-preparation pipeline. It involves a series of steps.

1. Data cleaning. Entries with empty or incorrect data have to be either removed or carefully dealt with via other methods such as data imputation. Data imputation refers to the process of filling in missing data values with estimated or predicted values based on the available data.
    
2. Data scaling. Data typically may contain several features with widely different ranges. That is, while the price of a product may experience fluctuations in the 10s of dollars, sales may experience variations in the 10000s of dollars. When the range of values of raw data varies widely, many ML algorithms will fail to work properly. Data scaling, also referred to as feature scaling, is then used to normalize the range of independent variables or features of data.
    
3. Other data transformations. Some other common data transformations include:
    
4. Removing outliers
    
5. Converting numerical variables (e.g., age of a person) to a categorical variable (is the person < 45?)
    
6. Transforming categorical variables into numerical inputs via one-hot encoding
    
7. Feature engineering. Feature engineering is the process of creating new features or modifying existing ones from raw data to improve the performance of ML models. This can involve a wide range of techniques, including:
    
8. Extracting relevant information from text, images, and other raw data sources.
    
9. Combining multiple features to create new ones.
    
10. Encoding categorical variables in a meaningful way.
    
11. Scaling or normalizing features to similar ranges.
    
12. Creating polynomial features to capture non-linear relationships.
    

The goal of feature engineering is to create features that are more informative, relevant, and useful for the task at hand, and thus lead to better model performance. Feature engineering is the art of employing domain-specific knowledge and combining it with available raw data to come up with “new” features that can help us to solve the problem at hand.

Extracting useful features from raw data is more art than science and this plays a critical role in improving the performance of ML algorithms.

For example, suppose we are building a ML algorithm to predict traffic on roads based on historic data of traffic over the past two years. A simple feature that we may want to “engineer” is to use the available date column to generate two new columns: (i) is the date a weekend?, (ii.) is the date a public holiday?

We will discuss feature engineering in this unit, and you will complete a feature engineering assignment as well. .