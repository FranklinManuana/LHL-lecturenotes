### Why Do We Care?

Missing data in a data set can reduce the power/fit of a model if treated as a real category, because:

- Some models ignore rows with missing values effectively reducing your sample size.
- It can lead to a wrong prediction or classification.
- Missing values do not always mean an empty field.

Let's take a look at a very simple example in the table below. In the left table, we have two missing values in the 'gender' column.

![](https://i.imgur.com/kiqqa5w.png)

If we don’t fill in the null values, our conclusion is that both women and men in the data are equally likely to play cricket.

However, when we fill in the missing values, based on the 'name' column, we get the actual result:

- Women – 75% play cricket
- Men – 50% play cricket

The null value replacement allows us to come to the more accurate conclusion that women are more likely to play cricket than men.

### How to Handle Missing Values

There are many different ways of dealing with missing values. It depends on the size of the data we have, the data type, or what model we want to use.

Instruction

Follow the article [Handling Missing Data](https://jakevdp.github.io/PythonDataScienceHandbook/03.04-missing-values.html) to learn the most popular ways of handling missing values.

