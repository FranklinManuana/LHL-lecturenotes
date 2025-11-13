We will now take a look at **stochastic gradient descent**. Although it sounds rather fancy, it is just a simple extension of the classic Gradient Descent.

Stochastic gradient descent (SGD) is a popular optimization algorithm used in machine learning for minimizing the cost or loss function of a model during training.

In traditional gradient descent, the cost function is minimized by iteratively adjusting the model parameters in the direction of the steepest descent of the cost function. This is done by computing the gradient of the cost function with respect to the model parameters using the entire training dataset, and then updating the parameters using this gradient. However, in stochastic gradient descent, the gradient is computed on a subset or mini-batch of the training data, rather than the entire dataset. This mini-batch is chosen randomly at each iteration, and the model parameters are updated using the gradient computed on this mini-batch. This results in a much faster convergence rate and a more efficient use of memory, as the algorithm doesn't need to process the entire dataset at once.

SGD is particularly useful when the dataset is large, and the computational resources available are limited. It is widely used in deep learning, where the cost function is often high-dimensional and non-convex, making traditional optimization algorithms infeasible.

Instruction

Follow the video below to learn more about _stochastic gradient descent_: