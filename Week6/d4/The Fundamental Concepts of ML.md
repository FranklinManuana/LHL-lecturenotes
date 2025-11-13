### Types of Machine Learning

Machine learning refers to a broad category of algorithms that are capable of performing various tasks. For example, predicting the future stock performance of a company given its historical financial data is an entirely different objective from identifying instances of financial mismanagement. Therefore naturally, the two problems call for an altogether different approach, with different algorithms and methods.

The term 'machine learning' is applicable as long as a ‘machine’ is necessary to parse large amounts of data and as long as the relationships between the various data values are ‘learned’ by an algorithm rather than being decided manually.

This reading describes the different types of ML algorithms based on the objective they are designed to achieve.

#### I. Supervised learning

Supervised learning is performed on data inputs along with their corresponding outputs or labels. The goal of supervised learning is to learn the underlying relationship between the inputs and outputs, based on historical data. Therefore, supervised machine learning refers to algorithms that ‘learn by example’. A common supervised learning task is to classify observations into two or more classes.

For example, in the following image, we depict an image recognition classifier which learns to classify images of fruits as either ‘apples’ or ‘not apples’. It learns to do so based on data comprising images of apples and other fruits with attached labels indicating which class each image belongs to. This is therefore a supervised learning task.

![Supervised learning apples, no apples to input and finding it is an apple](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/Fundamental-Concepts-of-ML-1.png)

As another example of a supervised learning task, Amazon developed an internal recruitment tool that was trained on past hiring data to automate hiring decisions. That is, the ML algorithm was trained on resumes of past job applicants (input) with attached labels signifying whether they ended up being hired or not (output).

#### II. Unsupervised learning

Unsupervised learning, on the other hand, does not have labeled outputs, so the goal is to infer some natural structure present within the data. It does so by searching for patterns within data and clustering observations that are similar to each other.

Unlike supervised learning, unsupervised learning operates upon only the input data without corresponding outputs or labels

For example, in this image, we depict an algorithm which is fed images of different fruits without corresponding labels signifying what fruit the image represents. The image recognition algorithm searches for patterns within the images and identifies groups of images that are similar to one another.

![Unsupervised learning unlabelled data in, and categorization out](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/Fundamental-Concepts-of-ML-2.png)

For example, retail stores provide loyalty cards enabling them to track customer purchasing history. They use customer sales data to segment them into groups or ‘clusters’ of customers with similar purchasing patterns such as regular and frequent shoppers, discount and bulk shoppers etc. This allows them to provide targeted coupons or offers. In the retail business, this is referred to as ‘Customer Segmentation’.

The main focus of this course will be on supervised and unsupervised learning. However, there are some other types of machine learning models and it will be useful to have a brief understanding of what they are.

#### III. ​Hybrid: Semi-Supervised learning

There are some hybrid approaches that draw from both supervised and unsupervised learning. One such approach is semi-supervised learning.

Semi-supervised learning is useful when there are very few labeled examples and a large number of unlabelled examples.

The goal of a semi-supervised learning model is then to make effective use of all of the available data, not just the labeled data as in supervised learning.

Making effective use of unlabeled data may require the use of or inspiration from unsupervised methods such as clustering. Once groups or patterns are discovered, supervised methods or ideas from supervised learning may be used to label the unlabeled examples or apply labels to unlabeled representations later used for prediction.

It is common for many real-world supervised learning problems to be examples of semi-supervised learning problems given the expense or computational cost for labeling examples.

An example of semi-supervised learning is the use of a limited amount of labeled data (such as customer feedback) and a large amount of unlabeled data (such as customer behavior data) to classify new customer feedback as positive or negative sentiment. The labeled data is used to train the algorithm, while the unlabeled data is used to refine and improve the accuracy of the classification model.

#### IV. Reinforcement learning

Reinforcement learning is the training of machine learning models to make a sequence of decisions in an uncertain and potentially complex environment.

In reinforcement learning, artificial intelligence faces a game-like situation. The model iteratively: - performs an action — receives a feedback for the actions it performs from the environment - uses the feedback to take future actions. Reinforcement learning can therefore be conceptualized as ‘learning by feedback’.

![Action and reward or penalty](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/Fundamental-Concepts-of-ML-3.png)

Reinforcement learning is learning by interacting with an environment. The algorithm learns from the consequences of its actions, rather than from being explicitly taught, and it selects its actions on the basis of its past experiences (exploitation) and also by new choices (exploration), which is essentially trial and error learning. This iterative process of action, feedback, and improvement carries on until the algorithm learns to successfully predict, or more generally, perform the task required of it.