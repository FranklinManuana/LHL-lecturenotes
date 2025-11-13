### Review of Linear Regression

Before we introduce logistic (binary) regression models, we need to review normal linear regression models. Let

Υi = β0 + β1xi1 + β2xi2 + ... + βpxip + εi

where εi for i = 1, ...n are independent and each has a normal probability distribution with mean 0 and variance σ2 . This leads to each Yi for i = 1, ... n being independent predictions with normal distributions. The β0, ... βp are regression parameters that quantify the relationship between the explanatory variables and Yi.

For example, if βi = 0, this says a linear relationship does not exist between the first explanatory variable and the response variable given the other variables in the model. Alternatively, if β1 > 0, a positive relationship exists (an increase in the explanatory variable leads to an increase in the response variable), and if β1 < 0, a negative relationship exists (a decrease in the explanatory variable leads to a decrease in the response variable).

Thus, if we have xi1, ..., xip (which we do, because it is our data) and somehow know all of the β0, ... βp , we can find out the value of Yi . Of course, we don’t know the actual values for β0, ... βp , but we can estimate these parameters using least squares estimations — and that is exactly what our linear regression model does.

In the context of binary classification (where the response is binary), the quantity we want to estimate is the probability of the response variable falling into a particular class. In academic terms, this is referred to as the probability of success, **pi**; .

### Logistic Regression

Consider now a binary response variable with possible values 1 and 0 corresponding to success and failure. In this case, the simple linear regression equation is no longer appropriate.

What do we do about it?

Enter the logistic regression model.

The logistic regression extends the right-hand side of the linear regression model, and defines the probability of success this way:

**pi** = eβ0 + β1xi1 + ... + βpxip / (1 + eβ0 + β1xi1 + ... + βpxip )

Notice that eβ0 + β1xi1 + ... + βpxip is always positive, and the numerator is always less than the denominator, which means that 0 < pi < 1.

The above definition of pi is also known as the logit function.

The graph of the logit function looks like this:

![Graph of the logit function](https://i.imgur.com/qJ6hlUr.png)

So now, the logistic regression model can be written as:

ln(pi/(1-pi)) = β0 + β1xi1 + ... + βpxip

Notice that the left-hand side of the equation above is the natural logarithm of the odds of success, which we will go over in greater detail in a later activity. The right-hand side of the equation above is essentially the same as the right-hand side of the linear regression equation.

This type of statistical model (also known as _logit model_) is often used for classification and predictive analytics. Logistic regression estimates the probability of an event occurring, such as voted or didn’t vote, based on a given dataset of independent variables. Since the outcome is a probability, the dependent variable is bounded between 0 and 1.

---