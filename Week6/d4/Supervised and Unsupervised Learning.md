### Supervised vs Unsupervised Learning

Supervised and unsupervised methods are two broad machine-learning approaches that we will discuss in-depth in future units in this course.

But, first, it is important to learn how to identify and distinguish between the two.

The following diagram shows the key distinctions between supervised and unsupervised learning.

![Classical machine learning diagram. In supervised learning, the data is already categorized or labelled, and it is task-driven. Regression and Classification tasks are types of supervised learning, resulting in predictions and predictive models. Unsupervised learning is data-driven, using unlabelled data. This results in clustering, association, or dimensionality reduction tasks, and helps in pattern or structure recognition.](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-1.png)

Instruction

Read the PDF copy of this Medium article called [Supervised vs Unsupervised Machine Learning](https://drive.google.com/file/d/1t4FTQZbOkKkKwJNNiAwjaG69tSqtfZlC/view?usp=drive_link) for further details.

Let’s review the items from the diagram in greater detail now.

### I. Supervised Learning

As we discussed in the last reading, Supervised learning is task-driven with clearly pre-defined objectives and based on data which is labeled and categorized.

It is used primarily for two objectives, classification and regression.

#### 1. Classification

In a classification problem, a set of already classified and labelled data is used to construct a machine learning model that can then classify unknown entities into the given classes.

![Classsification problem. In this case, Apples and items that are not apples are fed to the model. Then, an apple is introduced to the apple, and the model says that It's an apple!](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-2.png)

##### **An example of a classification problem:**

- **Image-recognition**: Imagine a program that identifies pictures of people (with a specific, well-defined objective such as identifying sex) that has been trained using a dataset of some labeled images of humans and some labeled images of non-human subjects There are a variety of classification algorithms, each with its assumptions, strengths and weaknesses. In this course, we will be discussing some of the prominent classification algorithms employed in the industry:
    - logistic regression,
    - decision trees, and
    - support vector machines.  
        

#### 2. Regression

In a regression problem, the goal is to model the relationship between one or more input features (independent variables) and an output feature (dependent variable) based on a set of training data. The model is trained on this data to learn the relationship between the input features and the output feature, and can then be used to make predictions on new, unseen data. In regression problems, the output feature is usually a continuous value, as opposed to a discrete class label in classification problems.

- **Discrete variable**: Discrete variables are values that can only take on certain specific numerical values. These values are distinct and separate from one another, meaning that they cannot be subdivided or take on decimal values. For example, the number of cars in a parking lot is a discrete variable, as it can only take on integer values (1, 2, 3, etc.) and cannot be fractional (1.5, 2.25, etc.).
- **Continuous variables**: Continuous variables are values that can take on any numerical value within a certain range or interval. Unlike discrete variables, continuous variables can take on fractional or decimal values, and there is no limit to the number of possible values within the range. For example, the weight of a person is a continuous variable, as it can take on any value between the minimum and maximum weight range, such as 50.3 kg, 65.8 kg, or 75.2 kg.

##### **An example of a regression problem:**

Given past marketing data and ad spends on different channels, we would like an algorithm that can determine the effect of ad spending on total sales of a product that can be employed for future marketing decisions. We can see this in the following image - using linear regression on past sales of a product against the ad spend on TV, radio, and newspaper allows us to infer the effects of marketing on sales.

![Using linear regression on past sales of a product against the ad spend on TV, radio, and newspaper allows us to infer the effects of marketing on sales.](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-3.png)

### II. Unsupervised Learning

Unsupervised learning is typically data-driven, i.e., ‘we let the data speak for itself’ and the job of the machine learning algorithm is simply to uncover underlying patterns inside the data.

Subsequently, humans with domain knowledge and experience can make sense of these underlying patterns uncovered by the unsupervised learning algorithm and interpret them.

Unsupervised ML algorithms are primarily used for three objectives: - clustering, - association learning, and - dimensionality reduction.

![The goal is to uncover underlying patterns and structure.](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-4.png)

#### 1. Clustering

Some of the main problems in this area are called clustering tasks. Loosely defined, the goal is to find patterns in large amounts of data by grouping together the entities which have similar features. For example, in the following image, we depict an algorithm which is fed images of different fruits without corresponding labels, signifying what fruit the image represents. The image recognition algorithm searches for patterns within the images and identifies groups of images that are similar to one another, i.e. images of the same fruit are grouped together.

![For example, here we depict an algorithm which is fed images of different fruits without corresponding labels signifying what fruit the image represents. The image recognition algorithm searches for patterns within the images and identifies groups of images that are similar to one another, i.e. images of the same fruit.](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-5.png)

##### **An example of a clustering problem:**

Another example of unsupervised learning is the Spotify ‘mood’ playlist – this algorithm identifies songs that share some similar characteristics and groups them into a playlist. Similarly, Twitter has recently begun to identify groups of similar tweets into ‘topics’ and recommends suggested topics for users to follow. You can see this in the following image.

![For You on Twitter is an example of a clustering problem.](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Intro%20to%20ML/Supervised-Unsup-6.png)

#### 1. Dimensionality Reduction

Sometimes, in machine learning, there is such a thing as a problem of plenty. We could have a dataset with, say, 200 columns – one for each input feature.

Dimensionality reduction attempts to reduce the number of input features to a more manageable number, say, 25.

Why do we need to do this? Why can we not feed in all the features into a machine learning algorithm?

There are many reasons why: - The more the number of input features, the more observations will be needed to train accurate models. - The more features a machine learning model uses, the greater the chances of over-fitting. - A large number of features will make the machine learning model more complex.Thus, it will require longer computation times and higher computation space.

Dimensionality reduction algorithms help us by selecting a subset of “important” features that are sufficient to perform the task at hand. While we do not discuss dimensionality reduction algorithms in this course, it is useful to know that these tools do exist in the machine learning universe to deal with the problem of ‘too many features’ in the data.

#### References

- D., Samuel. Supervised vs Unsupervised Machine Learning. March 25, 2020. Accessed Oct. 5th, 2020.  
    [https://medium.com/datadriveninvestor/supervised-vs-unsupervised-machine-learning-732d49413986](https://medium.com/datadriveninvestor/supervised-vs-unsupervised-machine-learning-732d49413986)

