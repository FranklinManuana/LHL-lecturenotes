## Generalized Linear Model (GLM)

We have seen previously that when we generalize logistic regression, we get multinomial regression. But we don’t have to stop there.

When we generalize multinomial regression, we get Generalized Linear Models (GLM).

Therefore, GLM is the generalized model, whereas logistic regression and multinomial regression are specific cases of GLM.

GLM is an umbrella term that encompasses many other models, which allows the response variable $y$ to have an error distribution other than a normal distribution. GLM includes Linear Regression, Logistic Regression, and Poisson Regression.

In a Linear Regression Model, the response (aka dependent/target) variable y is expressed as a linear function/linear combination of all the predictors x (aka independent/regression/explanatory/observed variables). The underlying relationship between the response and the predictors is linear (i.e. we can simply visualize the relationship in the form of a straight line). Also, the error distribution of the response variable should be normally distributed.

GLM models allow us to build a linear relationship between the response and predictors, even when their underlying relationship is not linear. This is made possible by using a **link function**, which links the response variable to a linear model. Unlike Linear Regression models, the error distribution of the response variable need not be normally distributed. The errors in the response variable are assumed to follow an exponential family of distribution (i.e. normal, binomial, Poisson, or gamma distributions).

### Components of GLM

There are three components in generalized linear models.

1. Linear predictor
2. Link function
3. Probability distribution

Let’s use logistic regression as an example to better understand these components. Recall the logistic regression model:

ln(pi/(1-pi)) = β0 + β1xi1 + ... + βpxip

where **pi** = eβ0 + β1xi1 + ... + βpxip / (1 + eβ0 + β1xi1 + ... + βpxip)

#### The Linear Predictor

The linear predictor component (also referred to as the systematic component) is simply the linear combination of the predictions and the regression coefficients. In the case of logistic regression, it is the following component of the equation:

β0 + β1xi1 + ... + βpxip

#### Link Function

The link function component specifies the link between the random and systematic components. It indicates how the expected/predicted value of the response relates to the linear combination of predictor variables.

In the case of logistic regression, the link function is the logit function.

#### Probability Distribution

The probability distribution component (also referred to as the random component) refers to the probability distribution, from the family of distributions, of the response variable. The family of distributions, called an exponential family, includes normal distribution, binomial distribution, or Poisson distribution.

This component makes GLM flexible.

### Assumptions of GLM

Similar to Linear Regression Model, there are some basic assumptions for Generalized Linear Models as well. Most of the assumptions are similar to Linear Regression models, while some of the assumptions of Linear Regression are modified.

- Data should be independent and random (each random variable has the same probability distribution).
- The response variable y does not need to be normally distributed, but the distribution is from an exponential family (e.g. binomial, Poisson, multinomial, normal)
- The original response variable need not have a linear relationship with the independent variables, but the transformed response variable (through the link function) is linearly dependent on the independent variables