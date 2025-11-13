In this reading, we will learn the best practices for splitting data before modeling.

## How to Resample Data Before Modeling

Instruction

Read the article [**How to Train a Final Machine Learning Model**](https://machinelearningmastery.com/train-final-machine-learning-model/) to understand the main motivation behind resampling our data before modeling.

Train/test splitting is a common practice in machine learning to evaluate the performance of a trained model on new or unseen data. The purpose of train/test splitting is to estimate how well the model will generalize to new data that it has not seen during training. When building a machine learning model, it is important to ensure that the model is not just "memorizing" the training data but is learning the underlying patterns that can generalize to new data. If we test the model on the same data that it was trained on, we might get a very high accuracy, but this would not be a good estimate of how the model would perform on new, unseen data.

Therefore, to evaluate a model's performance accurately, we split the available data into two sets: a training set and a test set. The model is trained on the training set, and its performance is evaluated on the test set. By testing the model on data that it has not seen during training, we get a better estimate of how the model would perform on new data. Moreover, train/test splitting is also used to tune model hyperparameters, such as the learning rate or regularization strength. By evaluating the model's performance on a separate validation set, which is another subset of the training data, we can choose the hyperparameters that result in the best performance on the validation set.

Instruction

Read about different options of splitting data in the PDF copy of this Towards Data Science article called [Cross-Validation in Machine Learning](https://drive.google.com/file/d/1x0FRsJUMsgR7gs8rwZQsmNEM0GVra5om/view?usp=drive_link).

If you are more comfortable with videos, you can also watch this tutorial:

### Best Practices

There are a couple of best practices that we can follow to make sure we choose the best approach:

- Use **the KFold cross-validation** in case we deal with a small amount of data. In this case, it is very costly to leave some observations as a hold-out set.
- In case we have enough data, the best practice is to use the combination of **a hold-out set** and **cross-validation**:
    1. Split the data into a train and a test (hold-out) sets.
    2. Apply cross-validation on the training set to find the optimal model.
    3. Test the model on the test set to see if the performance is good with a "new"(unseen) data.

The choice between KFold cross-validation and a combination of hold-out set and cross-validation depends on the size of the available dataset and the computational resources available. If we have a small dataset, using KFold cross-validation can be a good option because we cannot afford to have a large portion of the data as a hold-out set. In KFold cross-validation, the data is split into K folds, and the model is trained and tested K times on different subsets of the data. This helps to reduce the variance of the evaluation metric and gives a more reliable estimate of the model's performance.

On the other hand, if we have enough data, it is generally recommended to use a combination of a hold-out set and cross-validation. This approach allows us to evaluate the model's performance on a "new" data that it has not seen during training, using the hold-out set. Additionally, cross-validation on the training set helps to tune the model hyperparameters and get a more reliable estimate of the model's performance.

In general, a good rule of thumb is to use a hold-out set and cross-validation when we have enough data available, but use KFold cross-validation when the data is limited. However, it is important to note that there is no one-size-fits-all solution, and the choice between these options ultimately depends on the specific requirements of the problem at hand.