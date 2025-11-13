This unit will go into more detail about **supervised learning**. It's the most commonly used type of machine learning.

## Introduction to Supervised Learning

In _supervised learning_, we work with pairs consisting of _examples_ and _labels_.

![picture of a cat as an example with the word `cat` as a label.](https://i.imgur.com/HmbDspv.png)

In the image above, there's a picture of a cat as an example with the word `cat` as a label.

The goal of supervised learning is to train a model on a labeled dataset so that it can make accurate predictions on new, unseen data. The model is trained to map inputs to outputs based on the relationship between the features and labels in the training data, with the objective of minimizing the prediction error. So, the goal of _supervised learning_ is to find a magical function **`h`**, where `h(x) = y` for all world examples.

Unfortunately, it's a very complex problem and there is no easy solution. The "No Free Lunch" theorem, also known as NFL theorem, states that no single machine learning algorithm works best for all problems. In other words, there is no algorithm that is guaranteed to be optimal for every problem, and the best algorithm for a particular problem depends on the specific properties and characteristics of the problem and the data. This means that the choice of algorithm must be based on the understanding of the problem and the data, and requires careful experimentation and evaluation. The theorem highlights the importance of evaluating and comparing multiple algorithms for a given problem to determine the best one for that specific use case.

![No-Free-Lunch Theorem. There is no universal learner. It is inevitable to use prior knowledge for successful learning.](https://i.imgur.com/aF63vMw.png)

Instruction