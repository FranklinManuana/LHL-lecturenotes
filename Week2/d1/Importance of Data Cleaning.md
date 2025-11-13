### What Is Data Cleaning?

**Data cleaning** is a critical part of data analysis. The data cleaning process involves reviewing all the data present within a database (or other relevant systems) to either remove or update information that is incomplete, incorrect or duplicated, and irrelevant. Data cleaning also includes putting data that is the wrong format into the right one.

### Data Cleaning Methods

There are some considerations when it comes to data cleaning:

1. Remove Unwanted or Irrelavent Observations
    
    When you get the data, the first step in data cleaning is to remove the unwanted, duplicate, or irrelevant observations. Irrelevant observations are ones that do not fit with the problem statement you are trying to solve.
    
2. Ensure Accurate Datatypes
    
    Data types should be uniform across all of the datasets. A string can’t be termed as numeric nor can a numeric be a boolean value. Small mistakes are often made when numbers are entered. These mistakes can sometimes make the data unreadable and thus need to be changed to actual readable data.
    
3. Address Missing Values
    
    Correcting missing values is another important method that can’t be ignored. Knowing how to handle missing values will help keep the data clean. Sometimes, there may be too many missing values present in a single column. For such occurrences, there might not be enough data to work with, so deleting the column may stand as the best option in such cases. There are also other different ways to impute missing data values in the dataset. This can be done by estimating what the missing data might be and performing linear regression or replacing with the median value.
    
4. Fixing Typos
    
    Typos resulting from human error are often unavoidable and can be fixed through multiple algorithms and techniques. One of these techniques is mapping the values and converting them into their correct spelling. Fixing typos is an essential part of the data cleaning process as models will treat differently spelled words as unique values, even if that is not our intention. Strings present in data rely heavily on their spellings and cases.
    

Instruction

We would highly recommend reading more on data cleaning in this article [Cleaning and Transforming Data with SQL, Towards Data Science](https://drive.google.com/file/d/1XfkF9vEGDGvipAqoiEl8uHPOQe913pbn/view?usp=drive_link)

The insights that we draw from your data are highly dependent on the data itself, hence, no surprise that analytics professionals spent 80% of their time cleaning and transforming data for use in the analysis.

Note

It is worth mentioning that incorrect and inconsistent data can lead to false conclusions, and misdirect our decision-making process. Hence, it’s very important for us to clean up our data before we analyze it. When planning to clean data ask yourself the following questions:

- What will be the impacts of working with biased data?
- What will be the impacts of sharing wrong results and misleading conclusions?

### Conclusion

Having clean data will lay the foundation for your analysis, so It might be a good idea to make yourself a data cleaning checklist to follow as you start refining this skill!