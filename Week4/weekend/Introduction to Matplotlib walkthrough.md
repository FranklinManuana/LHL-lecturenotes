In this hands-on activity, we will focus on creating of multiple types of graphs with `Matplotlib` **stateful approach** (Functional). We will also learn how to customize the graphs with legends, annotations, and so on. Let's begin with importing the necessary libraries.

```python
import numpy as np

import matplotlib.pyplot as plt

# set the figure size for each figure in this tutorial
plt.rcParams["figure.figsize"] = (10,6)
```

### Line Plot

In this example, we will create a sine wave with an x-range from 0 to 100. We will generate data using `Numpy`.

```python
# 200 values from the interval <0,100>, equidistantly divided
x = np.linspace(0,100,200)
y = np.sin(x)

# a line plot
plt.plot(x,y,'red')
plt.show()
```

### Scatter Plot

```python
# 200 random values from the interval <0,10>
x = 10*np.random.rand(200,1)

# 200 random values from the interval <0,15>
y = 15*np.random.rand(200,1)

# a scatter plot 
plt.scatter(x,y)
plt.show()
```

### Histogram

```python
# 200 random values from the interval <0,15>
y = 15*np.random.rand(200,1)

# a histogram with 20 bins
plt.hist(y,bins=20)
plt.show()
```

Now that we know how to plot basic charts with `Matplotlib`, it's time to progress to some plot customizations.

### Graphs on Common Axes

In this example, we will plot two mathematical functions (sin(x), sin(x)*cos(x)) on one figure with shared axis.

```python
# 200 values from the interval <0,100>, equidistantly divided
x = np.linspace(0,100,200)

# sin(x) values
y1 = np.sin(x)

# sin(x)*cos(x) values
y2 =(np.sin(x))*(np.cos(x))

# a line plot of sin(x), red line
plt.plot(x,y1,'red')

# a line plot of sin(x)*cos(x), blue line
plt.plot(x,y2,'blue')
plt.show()
```

### Subplots

Let's continue with the example above but with one small change. Now we want to have a separate figure with its own axis for each function.

```python
# the first figure
plt.subplot(2,1,1)
plt.plot(x,y1,'red')
plt.title('sin(x)')

# the second figure
plt.subplot(2,1,2)
plt.plot(x,y2,'blue')
plt.title('sin(x)*(cos(x))')

# automatically adjust the subplot parameters to give a specified padding
plt.tight_layout()
plt.show()
```

The first two parameters of `plt.subplot()` are the shapes of a grid with figures. In our example, we created a grid with 2 rows and one column. If we want to have our figures side by side (1 row, 2 columns) we just simply swap these parameters. The third parameter is the index of the actual figure in which we are plotting. The index starts at 1 in the upper left corner of a grid and increases to the right.

### Legends

In the next two examples, we will use the famous Iris dataset. For this purpose, we have to import `Pandas` and `Sklearn` libraries.

```python
import pandas as pd

from sklearn import datasets
```

Load Iris data to a data-frame.

```python
# load iris dataset
iris = datasets.load_iris()

# create dataframe
iris_df = pd.DataFrame(iris.data, columns=iris.feature_names)

# create target
iris_df['target'] = iris.target

# map the target values to the target names
iris_df['target_name'] =iris_df.target.map(
    {0: 'setosa', 
     1: 'versicolor',
     2: 'virginica'}
)
```

Print the top 5 rows of the created data frame.

```python
iris_df.head()
```

Now, let's plot a scatter plot of sepal length and sepal width for each type of the Iris flower.

```python
# Iris setosa
setosa = iris_df[iris_df.target_name == 'setosa']

# Iris versicolor
versicolor = iris_df[iris_df.target_name == 'versicolor']

# Iris virginica
virginica = iris_df[iris_df.target_name == 'virginica']

# plot setosa
plt.scatter(setosa['sepal length (cm)'], setosa['sepal width (cm)'],
            marker ='o', color = 'red', label = 'setosa')

# plot versicolor
plt.scatter(versicolor['sepal length (cm)'], versicolor['sepal width (cm)'],
            marker ='o', color = 'green', label = 'versicolor')

# plot virginica
plt.scatter(virginica['sepal length (cm)'], virginica['sepal width (cm)'],
            marker ='o', color = 'blue', label = 'virginica')

# legend location
plt.legend(loc='upper right')

# plot title
plt.title('Iris flower')

# x-axis title
plt.xlabel('sepal length (cm)')

# y-axis title
plt.ylabel('sepal width (cm)')
plt.show()
```

By setting the `label` parameter in each scatter plot we set the name shown in the legend.

### Annotations

If we want to add annotations to the figure we created in the example above, we can do that by making the following changes in the code.

```python
# the same code as before
plt.scatter(setosa['sepal length (cm)'],setosa['sepal width (cm)'],
            marker ='o', color = 'red', label = 'setosa')

plt.scatter(versicolor['sepal length (cm)'],versicolor['sepal width (cm)'],
            marker ='o', color = 'green', label = 'versicolor')

plt.scatter(virginica['sepal length (cm)'],virginica['sepal width (cm)'],
            marker ='o', color = 'blue', label = 'virginica')

# new lines of code
# it can be tricky to find the right coordinates for the first time
######################
plt.annotate('setosa', xy =(5.0,3.5),
             xytext = (4.25,4.0), arrowprops={'color':'red'})
plt.annotate('virginica', xy =(7.2,3.6),
             xytext = (6.5,4.0), arrowprops={'color':'red'})
plt.annotate('versicolor', xy =(5.05,1.95),
             xytext = (5.5,1.75), arrowprops={'color':'red'})
######################

# the same code as before
plt.legend(loc='upper right')
plt.title('Iris flower')
plt.xlabel('sepal length (cm)')
plt.ylabel('sepal width (cm)')
plt.ylim(1.5,4.7)
plt.show()
```

To add annotations we used the `plt.annotate()` function. The `xy` parameter is a tuple containing the position to which the arrow is pointing. The `xytext` is a tuple containing the position where the text of the annotation is placed.