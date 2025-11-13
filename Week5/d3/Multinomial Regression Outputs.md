In this activity, we will go over the multinomial regression output we generated in the previous activity:

![multinomial logit output table](https://i.imgur.com/aaFuWdT.png)

### Understanding the Model Output

When fitting a multinomial regression model, the outcome has several (more than two or K) outcomes, which means that we can think of the problem as fitting K-1 independent binary logit models. The statsmodel module will also use one of the outcomes as a reference group. This means that when reading the statsmodels module's output, you will see that it only has K-1 sections (instead of K sections) due to the use of one of the outcomes as a reference group.

In the abalone example, there are three outcomes (female, infant, and male), and the reference group was chosen to be female. Therefore, our output from the model will show the information in two sections, one for SEX = Infant and one for SEX = Male.

Since logistic regression is a special case of multinomial regression where K = 2, you will want to pay attention to the same statistics in the model output:

1. **Log-Likelihood :** the natural logarithm of the Maximum Likelihood Estimation (MLE) function. MLE is the optimization process of finding the set of parameters that result in the best fit.
2. **LL-Null :** the value of log-likelihood of the model when no independent variable is included(only an intercept is included).
3. **P>|z| (or the p-value)**: A p-value of less than 0.05 is considered to be statistically significant.
4. **coef :** the coefficients of the independent variables in the regression equation.

---

