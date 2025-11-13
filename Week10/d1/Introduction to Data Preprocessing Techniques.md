In this reading, you will recall/learn different data preprocessing techniques that you used in the previous courses to refine your data and prepare it in the right format.

## Reading

Data preprocessing is a critical step in the data analysis and ML pipeline. It involves transforming raw data into a format that is more suitable for modelling.

If you can recall from previous lessons, there were several methods you applied to get your data in the right format before you could proceed to any ML tasks. Some of the preprocessing steps you learned previously were:

### Data Cleaning

**Handling Missing Values**: Missing data can be handled by removing the row, filling the missing value with a statistical measure (mean, median, or mode), or using an algorithm to predict the missing values.

_Example_: If you have a dataset of house prices with missing values in the 'number of bathrooms' feature, you might fill in the missing values with the median number of bathrooms.

**Noise Filtering**: This involves smoothing out the noise in the data which may be caused by errors in data collection.

_Example_: Applying a moving average filter to a noisy time series dataset to smooth out short-term fluctuations and highlight longer-term trends.

### Data Transformation

**Normalization**: Adjusting the scale of data so that it falls within a small specified range, such as 0 to 1, or -1 to 1.

**Standardization (Z-score normalization)**: Transforming data to have a mean of 0 and a standard deviation of 1.

**Encoding**: Converting categorical data into a numerical format.

_Example_: Using one-hot encoding to transform a categorical feature like 'color' with values 'red,' 'green,' and 'blue' into three binary features.

### Data Reduction

**Dimensionality Reduction**: Reducing the number of variables under consideration.

_Example_: Using principal component analysis (PCA) to reduce the dimensionality of a dataset with many interrelated variables to a set of uncorrelated variables.

**Binning**: Transforming continuous numerical features into categorical bins.

_Example_: Converting ages into discrete bins like 0-20, 21-40, etc.

### Feature Extraction and Selection

**Feature Extraction**: Creating new features from the existing ones to improve the predictive power of the model.

_Example_: Creating a feature called 'area' from 'width' and 'height' features for a dataset containing real estate information.

**Feature Selection**: Selecting the most significant features from the dataset to contribute to the output feature.

_Example_: Using a feature importance score from a model like Random Forest to select the top k features most important for predicting the target variable.

### Handling Imbalanced Data

Techniques such as over-sampling the minority class, under-sampling the majority class, or using synthetic data generation methods like Synthetic Minority Over-sampling TEchnique (SMOTE) can be used.

_Example_: In a dataset where 90% of the data belong to one class and the remaining 10% to another, you could duplicate some of the 10% class entries to balance it out.

Note

**Data Preprocessing for NLP Tasks**: There are additional types of data preprocessing techniques when dealing with and preparing textual data specifically for NLP tasks.

These techniques are important to get your data in the right format to be accepted into a model. You will learn more about these techniques in the section _Text Data Preprocessing_.

### Text Data Preprocessing

**Tokenization**: Breaking text into words, phrases, symbols, or other meaningful elements called tokens.

_Example_: Splitting a sentence into individual words.

**Stop Word Removal**: Removing common words that add little value to the analysis.

_Example_: Removing words such as 'and,' 'the,' 'is' from the text data.

**Stemming**: Crude method to find the stem of a word, oftentimes by chopping off common suffixes. May sometimes lead to incorrect words.

_Example_: _singing_ becomes _sing_.

**Lemmatization**: Aims to find the root word based on linguistics. It is more computationally expensive than stemming but may preserve context of words.

_Example_: _singing_, _sang_, _sung_ all become _sing_.

External Resource

Read [03: Basic Text Preprocessing (NLP)](https://drive.google.com/file/d/1rFQzNMoOBVFbsDP-MvNXULAGwz4Lsiyf/view?usp=drive_link) to learn more about text preprocessing techniques.

## Conclusion

Now that you have learned the basics of text data preprocessing, you will use them to preprocess a sample dataset in the next activity.