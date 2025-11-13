In this material, we are going to learn more about **Linear Regression**. Even though some people don't consider Linear Regression to be ML, it is a valid predictive algorithm that is very often used in real-world scenarios. It provides a perfect cornerstone for understanding other ML algorithms.

Linear regression is a statistical method used to model the relationship between a dependent variable and one or more independent variables. It is a type of regression analysis where the goal is to find a linear equation that best fits the relationship between the variables. In simple terms, linear regression is used to find a straight line that best describes the relationship between two variables. The line is defined by an equation of the form y = mx + b, where y is the dependent variable, x is the independent variable, m is the slope of the line, and b is the intercept. The slope represents the rate of change of the dependent variable with respect to the independent variable, while the intercept represents the value of the dependent variable when the independent variable is equal to zero. The goal of linear regression is to find the values of m and b that minimize the difference between the predicted values and the actual values of the dependent variable. This is done by using a method called least squares, which involves minimizing the sum of the squared differences between the predicted and actual values. Once the equation of the line has been determined, it can be used to predict the value of the dependent variable for any given value of the independent variable.

## Linear Regression

For our regression problem, we can define the loss function as:

![l(w^T x, y)=(w^Tx-y)^2](https://i.imgur.com/NLOdjoE.png)

We can then rewrite the function `h` from the previous reading to:

![w=arg min {1/n nΣi=1(w^Tx^(i)-yi)^2](https://i.imgur.com/z4fMOCw.png)

We are looking for a vector `w` which minimizes our loss. We know that we can do that by setting the `Gradient = 0`. We will do a derivative using `w` and we will get:

![2/n is cancelled out in formula. What remains is nΣi=1*x^(i)(w^T x^(i) -yi)=0](https://i.imgur.com/uV7FR8Q.png).

By simplifying this equation, we get:

![w=(XX^T)+Xy](https://i.imgur.com/PD4wxyq.png).

We call this **the method of least squares**.

Instruction

To better understand what is going on in the background, follow the video below:

Instruction

...and this one: 

---