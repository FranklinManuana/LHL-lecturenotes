## Filter Methods

_Filter feature selection methods_ apply a statistical measure to assign a score to each feature. The features are ranked by the score and either selected to be kept or removed from a dataset. The methods are often univariate and consider the features independently, or with regards to the dependent variable. This is what the flow of the process looks like:

![Set of all features to selecting the best subset to learning algorithm to performance.](https://i.imgur.com/K4Xu3nP.png)

Some common _filter methods_ used for feature selection are:

- Too high variance
- Too low variance
- By feature similarity (based on r^2 score)
- Chi-squared test
- Anova
- Correlation coefficient scores

We can use the following tree to find out the right _feature selection method_ based on the `target` variable type and feature type.

![Tree that shows selecting of feature selection method. Input variable is either numerical or categorical. If numerical, the output variable must be numerical or categorical. If Numerical, use Pearson's or Spearman's. For Categorical, use ANOVA or Kendall's. For a Categorical Input variable, Output variable is either Numerical or Categorical. Numerical is either ANOVA or Kendall's. Categorical is either Chi-squared or Mutual information.](https://i.imgur.com/JLPzxbs.png)

Instruction

We can learn more about _filter selection techniques_ in the article [**How to choose a feature selection method for Machine Learning**](https://machinelearningmastery.com/feature-selection-with-real-and-categorical-data/).