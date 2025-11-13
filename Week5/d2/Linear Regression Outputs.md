## Linear Regression Outputs

From our last activity of building a simple linear regression model using the Python `statsmodel` package, we have obtained the following output:

![linear regression output](https://i.imgur.com/HhE10f1.png)

Recall that our simple linear regression was built using `AveRooms` as the independent variable, and `MedHouseVal` (value of the house) as the dependent variable. Because there was only one independent variable in the linear regression model, this is a simple linear regression.

### Understanding the Model Output

In the model output above, you should pay attention to the following statistics in this order:

1. **R-squared**: R-squared reflects the fit of the model. R-squared values range from 0 to 1, where a higher value generally indicates a better fit, assuming certain conditions are met. In this output, we can see that the value is 0.681. This means that the model is capable of explaining 68.1% of the patterns in the data.
2. **P>|t| (or the p-value)**: A p-value of less than 0.05 is considered to be statistically significant. This regression output shows a p-value of 0, which means that the probability of the relationship between the average room size and median house value being solely due to natural variation is 0. In other words, the average room size does impact the median house value.
3. **coef**: Coef is short for the coefficient of the independent variable. It represents the impact on the response variable per unit increase of the independent variable. In this case, we can see that the coef of AveRoom has a value of 0.3277. This means that a unit increase in the value of AveRoom will have a positive impact on the MedianHouseVal.