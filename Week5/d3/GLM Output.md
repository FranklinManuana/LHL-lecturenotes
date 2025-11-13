## GLM Outputs

From the previous activity, after running the GLM model by Bonimial distribution, we obtained the following results:

![GLM output](https://i.imgur.com/ms2MM2k.png)

The model output above has identified the list of independent variables (LOWINC, PERASIAN, PERBLACK, etc.) to predict the dependent variable (SUCCESS).

It also indicates the following

- the model we built was a generalized linear model (GLM)
- we used the Binomial distribution as the probability distribution
- we used the logit function (the default function) as the link function.

You will notice that the output follows a very similar format to earlier models that we have built, and shows the coefficient for each variable, as well as their p-value.

One thing to note is that the p-value for all of the variables is very high. Since the p-value is the probability of obtaining results at least as extreme as the observed results of a statistical hypothesis test while assuming that the null hypothesis is correct, a high p-value indicates that we have no evidence to suggest an effect on the response variable.

This model output shows that the GLM, as constructed for the particular STAR 98 data set, is a poor model.

So what can we do about it?

The first thing we can do is revisit the EDA process. Are there additional steps required to clean the data? Or perhaps more data exploration will shed light on what data transformation will reveal the relationship between the independent and dependent variables.

The important thing to remember is that the data analytics process is iterative in nature. A failed model is not a bad thing as it forces us to revisit an earlier process, such as EDA, which creates an opportunity for us to discover insightful observations in addition to novel ideas for transforming variables and generating new ones.

---
