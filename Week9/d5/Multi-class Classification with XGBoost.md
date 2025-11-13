The approach that XGBoost takes for multi-class classification is called the "one-vs-all" or "one-vs-rest" approach.

In this approach, the XGBoost algorithm trains one binary classification model for each class in the target variable. For example, if you have a target variable with three classes (A, B, and C), XGBoost would train three binary classification models:

- Model 1: Classify whether an observation is in class A or not (i.e., B or C)
- Model 2: Classify whether an observation is in class B or not (i.e., A or C)
- Model 3: Classify whether an observation is in class C or not (i.e., A or B)

During the prediction phase, each model is used to predict whether an observation belongs to its respective class or not. The predicted probabilities for each class are then combined to determine the final predicted class for the observation.

XGBoost uses a softmax function to convert the predicted probabilities into class probabilities that sum to one. The class with the highest probability is then selected as the predicted class.

In summary, XGBoost performs multi-class classification by training multiple binary classification models and combining their predictions using a softmax function. This approach has been shown to be effective for a wide range of multi-class classification problems.

## Resources

To learn more about multi-class classification with XGBoost, review the following resources:

- [Multiple Outputs](https://xgboost.readthedocs.io/en/stable/tutorials/multioutput.html) - Starting from version 1.6, XGBoost has experimental support for multi-output regression and multi-label classification with Python package.
- [Demo for creating customized multi-class objective function](https://xgboost.readthedocs.io/en/stable/python/examples/custom_softmax.html)