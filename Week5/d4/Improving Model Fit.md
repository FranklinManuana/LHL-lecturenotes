Once you have gained an understanding of how well your model fits the data, it would be useful to know how to make it fit even better. Below we discuss two methods that can be used to do so.

### General Methods of Subset Selection

Suppose we have a dataset of **n** columns (**n** variables). To perform the best selection, the general method to achieve this is that we would fit separate models for each possible combination of the $n$ predictors, and then select the best subset. That is, we fit:

- All models that contain exactly one predictor
- All models that contain 2 predictors at the second step
- All models that contain 3 predictors
- …
- Until the end, where we build a model where all predictors are included

This results in 2^n possibilities as this is a _power set_ problem. When the dataset is wide (namely, when the number of columns is large), this general method will be impractical, as we will have too large of a number of combinations of columns that we will have to build. Thus, for computational reasons, the best subset cannot be applied for any large **n** due to the 2^n complexity. Enter forward stepwise selection!

### Forward Stepwise Selection

_Forward Stepwise_ begins with a model containing no predictors, and then adds predictors to the model, one at a time. At each step, the variable that gives the greatest _additional_ improvement to the fit is added to the model.

Under the Forward Stepwise selection method, a variable is added to the model only after we have evidence that model performance is improved if that variable is added in. In addition, variables are added to the model one at a time.

This method uses the regression model output and focuses on the p-value columns. Read your [p-value](https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/p-value/) first. If the p-value of a coefficient is small (less than your [alpha level](https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/what-is-an-alpha-level/)), you would not include that variable in the model. Otherwise, you would include it.