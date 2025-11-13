In this reading, we will get familiar with the concepts of **Variable Selection**, which is also a very valuable process of reducing the dimensions of our data before modeling.

Variable selection is a process in which a subset of features from a larger set of features are selected for use in a machine learning model. The goal of variable selection is to choose the most important or relevant features that provide the best predictive power for the model.

## Introduction to Variable Selection

The PCA creates `k` principal components that replace our created features. We shouldn't use both the original features and our components together.

The idea behind _the Variable Selection_ is to pick the existing features instead of generating new ones. We can use different _Variable Selection_ techniques to select `k` best features which will give us the best predictive power.

It is important to mention that it is not always the case that we should not use both the original features and the principal components together. In some cases, it might make sense to use both the original features and the principal components as input to a machine learning model. The choice of whether to use only the original features or both the original features and the principal components depends on the specific problem at hand and the results of experimentation.

We have two main types of techniques:

- Filter methods
- Wrapper methods

We are going to take a look at the most popular of these methods.

---