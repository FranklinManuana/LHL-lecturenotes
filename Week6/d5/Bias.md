One problem of ML, if it isn't done correctly, is `bias`. That's why we dedicate a separate reading to it. If our data are _biased_ we are going to end up with wrong predictions, so we should pay a lot of attention to avoid it.

## Reading

Instruction

Let's start with an example. Read the article [**Amazon scraps secret AI recruiting tool that showed bias against women**](https://www.reuters.com/article/us-amazon-com-jobs-automation-insight/amazon-scraps-secret-ai-recruiting-tool-that-showed-bias-against-women-idUSKCN1MK08G).

For an easier understanding of the concept, we can simplify the problem from the article: When the current ratio of men and women in tech companies is 7:3, it's very easy to build a model that says that men are a better fit for the role. However, this is not a correct solution and we call this _bias_.

Instruction

To see some options of dealing with _bias_ read [**Three ways to avoid bias in machine learning**](https://techcrunch.com/2018/11/06/3-ways-to-avoid-bias-in-machine-learning/). We would especially like to stress out the point no. 2: **Choose a representative training data set!**

To make things a little bit more complicated, we need to mention that _bias_ can also mean an error in training data. If we fit everything perfectly we say our model has very small _bias_. However, this leads to _overfitting_. We will learn more about overfitting later on.

Instruction

Follow the video below to better understand _bias_.