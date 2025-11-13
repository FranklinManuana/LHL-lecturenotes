## Classification Models

The simple linear regression model is appropriate for relating a quantitative response variable, y, to a quantitative predictor, x.

But now, consider now a binary response variable with possible values 1 and 0 corresponding to success and failure. In this case, the simple linear regression equation is no longer appropriate.

Classification models belong to the class of [conditional models](https://www.statlect.com/fundamentals-of-statistics/conditional-models) that is, probabilistic models that specify the [conditional probability distributions](https://www.statlect.com/fundamentals-of-probability/conditional-probability) of the output variables given the inputs. In classification models, the output has a discrete probability distribution (as opposed to regression models, where the output variable is continuous).

### Types of Classification Models

There are two flavours of classification models:

#### 1. Logistic regression model for binary classification

In this flavour, the output variable has a [Bernoulli distribution](https://www.statlect.com/probability-distributions/Bernoulli-distribution) conditional on the inputs. A Bernoulli random variable can take only two values, either 1 or 0, so a binary model is used when the output can take only two values.

For example, if the output variable is pass or fail, then it can be represented as a Bernoulli random variable that takes a value of 1 for pass and 0 for fail. It can also be represented as a random vector that takes the value of [1, 0] as pass, and [0, 1] as fail.

#### 2. Multinomial regression models for multinomial classification

In this flavour, the output has a [Multinomial distribution](https://www.statlect.com/probability-distributions/multinoulli-distribution) conditional on the inputs. Multinomial regression is a generalization of logistic regression. It can be used to model outputs that can take two or more values. If the output variable can take different values, then it is represented as a Multinoulli random vector, that is, a random vector whose realizations have all entries equal to 0, except for the entry corresponding to the realized output value, which is equal to 1.

For example, if the output variable can belong to one of three classes (red, green or blue), then [1, 0, 0] will represent red, [0, 1, 0] will represent green, and [0, 0, 1] will represent blue.

Note

Generalized linear model (GLM) is a generalization of multinomial regression, and logistic regression is a specific case of GLM. More about GLM later!