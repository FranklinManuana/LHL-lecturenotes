In the past reading, we became familiar with the regression model evaluation metrics. Because the same metrics won't do for classification problems it's time to add **the classification model evaluation metrics** to our knowledgebase.

Let’s learn about different classification model metrics.

- **Accuracy**: Accuracy is a measure of how well a classification model is able to correctly predict the class labels of the data instances in a dataset. It is defined as the ratio of the number of correct predictions to the total number of predictions made by the model.
- **Precision/Recall**: Precision and recall are evaluation metrics used for binary classification models. Precision is the ratio of true positives (TP) to the sum of true positives and false positives (FP), while recall is the ratio of true positives to the sum of true positives and false negatives (FN). Precision measures the proportion of positive predictions that are correct, while recall measures the proportion of actual positive instances that were correctly identified by the model.
- **F1-score**: The F1-score is a harmonic mean of precision and recall. It provides a single score that takes into account both precision and recall. The F1-score is a useful metric when we want to balance precision and recall, as it gives equal weight to both metrics. The F1-score ranges from 0 to 1, with a score of 1 indicating perfect precision and recall.
- **ROC curve/AUC score**: The receiver operating characteristic (ROC) curve is a plot of the true positive rate (TPR) against the false positive rate (FPR) at various classification thresholds. The area under the ROC curve (AUC) is a metric that measures the overall performance of a binary classification model across all possible thresholds. A higher AUC score indicates better model performance.
- **Log-Loss**: Log-loss is a loss function used in binary classification models that measures the accuracy of the model's probability estimates. It is the negative log-likelihood of the true labels given the predicted probabilities. A lower log-loss indicates better model performance, with a perfect model achieving a log-loss of 0. ## Classification Evaluation

Instruction

Read the PDF copy of this Towards Data Science article called [Understanding Data Science Classification Metrics in Scikit-Learn in Python](https://drive.google.com/file/d/1JIIAVm8asgDa1h7FushWK1eYTOdhaTJp/view?usp=drive_link) to learn more about these metrics and how you can apply them in python.

## Conclusion

There are many different techniques we can use for both: regression or classification algorithms. Often it's not easy to say which one is the best so we need to remember: always evaluate your model with more than one.