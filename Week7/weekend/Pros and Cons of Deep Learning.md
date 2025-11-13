Before digging deeper into the concepts behind Neural Networks and Deep Learning, we will look at the main advantages and disadvantages of Deep Learning in comparison with traditional Machine Learning.

## Pros and Cons of Deep Learning

Instruction

Read about the reasons why neural network algorithms are so popular in [**this article**](https://dev.solita.fi/2018/02/12/deep-learning-popularity.html). It also explains their biggest disadvantages.

Deep Learning allows us to handle data that in ways that aren't possible to do with classic ML models, such as like speech, images, or videos. These are the fields where deep learning brings the most value.

On the other hand, industries that need classic binary classification or regression for:

- credit scoring
- propensity-to-buy models
- likelihood of conversion
- churn prediction
- etc

are still using traditional ML techniques, as they are much easier to create, interpret, and maintain. Furthermore, with common tabular data (those we can store in a Pandas data-frame) they often return similar or better results than complex deep learning networks. For example, `XGBoost` can boast many success stories from various Kaggle competitions, where it proved to be the best model for many predictive tasks.

## Conclusion

We can sum up this topic as follows:

- For tabular data, using traditional ML can bring the most value (even when DL outperforms ML).
- For unstructured data, such as images, speech, videos, or text, DL offers big improvements.