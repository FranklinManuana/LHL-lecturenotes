## Class Imbalance

_Class imbalance_ means that the classes in our data are not equally distributed. Let's take a look at fraud prediction as an example. It is normal that there's 1% of frauds and the rest are normal observations. In this case, it will be very hard for a model to learn what is **fraud**. We have to take care of this by **resampling**.

Instruction

Read [**8 Tactics to Combat Imbalanced Classes in Your Machine Learning Dataset**](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/).

There are many options for handling class imbalance but we never know in advance which one will be the best for a particular problem. It is always about the investigation.

As a rule of thumb, if we have enough data and time to try only one approach, we can start by undersampling the class with a bigger occurrence. The **most important** thing to remember is: **ALWAYS** test the model on a test set with the right proportions. We can do anything we want with the train set as long as we can test the model on the correct representation of real life.

To address class imbalance, various techniques such as resampling, weighting, and threshold adjustment can be used.

1. Resampling: This involves either oversampling the minority class or undersampling the majority class. Oversampling can be done by duplicating observations from the minority class, while undersampling involves randomly removing observations from the majority class. This can help balance the distribution of classes in the dataset.
    
2. Threshold adjustment : Threshold adjustment is a technique used to improve the performance of machine learning models on imbalanced datasets. In a binary classification problem with imbalanced classes, the default threshold for classification is 0.5, which means that a predicted probability greater than or equal to 0.5 is classified as positive, and a predicted probability less than 0.5 is classified as negative. However, in imbalanced datasets, adjusting the threshold can improve the performance of the model on the minority class. For example, if the minority class is the positive class, a lower threshold may be used to increase the sensitivity of the model and reduce the false negative rate. This means that more observations from the minority class will be correctly classified as positive. On the other hand, if the majority class is the positive class, a higher threshold may be used to increase the specificity of the model and reduce the false positive rate. This means that fewer observations from the minority class will be incorrectly classified as positive.
    

---

