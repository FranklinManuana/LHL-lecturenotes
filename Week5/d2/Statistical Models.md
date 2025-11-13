As data analysts, we analyze data with the following 2 goals in mind:

- To understand what happened in the data - part of how we understand what transpired in the past is by spotting patterns in the data.
- To understand the state of the whole - using a representative sample from the past, we try to make a reasonable inference about the population.

## What Is Statistical Modelling?

**Statistical modelling** is the process of applying statistical analysis to a dataset. A **statistical model** is a mathematical representation (or mathematical model) of observed data.

When data analysts apply various statistical models to data, they are able to understand and interpret the information more strategically. Rather than sifting through the raw data, this practice allows them to identify relationships between variables, make predictions about future sets of data, and transform the data into visualizations so that non-analysts and stakeholders can consume and leverage it.

George Box, a prominent 20th-century statistician, has a famous quote: “All models are wrong, but some are useful.”

There have been countless models developed in the world of science to explain physical situations:

- Hooke’s Law explains the relationship between the length of an extended spring and the mass hanging from the end of it
- Newton’s laws include the famous “force = mass × acceleration.”
- Einstein’s E= mc^2

These are all examples of deterministic models because the left-hand side of the equation is completely determined or explained by the right-hand side.

While deterministic models are exact, statistical models are a little different because **statistical models** have an added component. In addition to the deterministic component, there is also a random component.

The random component occurs for a variety of reasons: measurement error, unaccounted, and natural variability. An example of natural variability is the height of people - different people have different heights. But even if you measured the same person twice you would get slightly different results. That’s measurement error.

### Objectives of Model Building

We define a model as a mathematical description of a real-world phenomenon. So what are the objectives of building a model?

- To provide a simple but adequate description of data
- To compare different sets of data
- To test a theory about a relationship
- To make predictions
- To give margins of error around estimates, predictions, and conclusions
- To understand the process that generated the data

### Steps of Model Building

#### Step 1. Model Selection: Formulating Statistical Analysis

Statistical analysis cannot be done without first knowing the following:

What type of variables are in the data? Variables play different roles and knowing the variable’s _type_ is crucial to knowing what to do with it and what it can tell us. The simplest and most important way to classify variables (and data) is either as _categorical_ or _quantitative_. What is each variable’s role? You need to know which variables are the predictors and which are the outcomes

Once those two pieces of information are clear, you can pick the statistical model that applies to that situation.

In the model selection step, plots of the data, process knowledge and assumptions about the process are used to determine the form of the model to fit to the data.

#### Step 2. Model Fitting: Applying Statistical Analysis

Using the selected model and possibly information about the data, an appropriate model-fitting method is used to estimate the unknown parameters in the model.

#### Step 3. Model Validation: Evaluating Assumptions and Conditions

When the parameter estimates have been made, the model is then assessed to see if the underlying assumptions of the analysis are reasonable. If the assumptions seem valid, the model can be used to answer the questions that prompted the modeling effort. If the model validation identifies problems with the current model, however, then the modelling process is repeated using information from the model validation step to select and/or fit an improved model.

## Conclusion

These three basic steps (model selection, fitting, and validation) are used iteratively until an appropriate model for the data has been developed.