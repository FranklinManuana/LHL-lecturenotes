## Multivariate Regression Outputs

From our last activity of building a multivariate linear regression model using the Python statsmodel package, we have obtained the following output:

![multivariate regression output](https://i.imgur.com/5I8ZGFT.png)

Recall that our multivariate linear regression was built using all of the columns in the data as the independent variables, and MedHouseVal (value of the house) as the dependent variable.

### Understanding the Model Output

As you may be able to see, this output is very similar to the output from the simple linear regression. In the case of multivariate regression, you should pay attention to the following statistics in this order:

1. **Adj. R-squared**: With multivariate regression, it is important to look at the ADJUSTED R-squared values as opposed to just R-squared as each added independent variable will increase the R-squared. Adjusted R-Squared takes into account the number of independent variables in the model and will give a more accurate view of how well the model can fit the data. In this particular case, R-squared and the Adj. R-squared are the same, but in general, this won’t always be the case. Our multivariate model explains 60.6% of the variations in the data.
2. **P>|t| (or the p-value)**: all of the p-values are 0 except for the p-value for Population, which has a value above the 0.05 threshold. This means that the relationship between population and median house value is most likely due to natural variation and it should be removed from the model. If you chose to remove population data from the model, you will notice that the fit, or adj R- squared, will increase.
3. **coef**: multivariate regression outputs will have a coefficient for each independent variable. Some are positive and some are negative. What we can tell from this output is that the average bedroom size has the strongest positive impact on median house value, whereas longitude (i.e location) has the largest negative impact on median house value.