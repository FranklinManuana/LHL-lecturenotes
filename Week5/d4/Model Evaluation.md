Applying a model will always result in an output that can be interpreted. Whether or not that interpretation has value depends on how good the model fits the data. This is often called the **goodness of fit** of the model.

For classification and regression models, there are specific outputs we look at to determine the goodness of fit.

### Regression Model Evaluation

#### R-Squared

R-squared is the measurement of how much of the dependent variable is explained by changes in our independent variables. A higher R squared means that our model fits the data well.

For multivariate linear regression, you should look at **Adjusted R-squared** instead of R-squared. The adjusted R-squared _adjusts_ the R-squared formula based on the number of variables, therefore a lower adjusted score may indicate that some variables are not contributing to your model’s R-squared properly.

#### p-value

The p-value column in the model output shows the effect of each variable on the outcome. If a variable has a p-value greater than the threshold value of 0.05, this may indicate that the variable should be removed from the model in order to get a better model fit.

#### F-Statistic

Included in the model output software is a hypothesis test where the null hypothesis is that all independent variables in the model have a coefficient of 0. We call this the null model. The F-statistic is related to this null model. Based on a chosen value of alpha, and [using an F-table](https://www.statisticshowto.com/tables/f-table/), we can determine if the null hypothesis is accepted or rejected. Rejecting the null hypothesis means that the coefficients of the independent variables are not all 0.

#### Prob (F-statistic)

Prob (F-Statistic) tells you the probability that your null hypothesis is correct. If the value of Prob (F-statistic) is 0, then your null hypothesis can be rejected.

### Classification Model Evaluation

#### p-value

The p-value column in the model output shows the effect of each variable on the outcome. If a variable has a p-value greater than the threshold value of 0.05, this may indicate that the variable should be removed from the model in order to get a better model fit.

#### Log-Likelihood, LL-Null, and LLR p - value

The Log-Likelihood (or LL) is the natural logarithm of the Maximum Likelihood Estimation (MLE) function. MLE is the optimization process of finding the set of parameters that result in the best fit.

LL-Null is the log likelihood of the null model. Similar to the null model in the regression output, the null hypothesis in the classification model is that all the variables have a coefficient of 0.

Log-likelihood and LL-Null can not be examined by their own individual magnitudes. Rather, we use the LLR p-value to interpret these outputs and gain insight into the model fit.

LLR p-value shows the probability that the null hypothesis is correct. If the p-value is large, that means the null hypothesis cannot be rejected and our model has a poor fit.

#### Confusion Matrix

The confusion matrix along with many other model evaluation metrics for classification models stands on the thin line between statistical modelling and machine learning. If you are interested in reading more about these metrics, take a look at [this resource](https://www.ritchieng.com/machine-learning-evaluate-classification-model/).