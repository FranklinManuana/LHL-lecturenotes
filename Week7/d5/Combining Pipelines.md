Let's now learn how to combine two pipelines together. We will use class `FeatureUnion` from `sklearn`.

## Tutorial

In real-life applications, we often use more than one feature extraction method and combine the results. We use the combination of these features as an input for our models. In this tutorial, we show how to combine features obtained by PCA and univariate selection inside a pipeline.

Note

This tutorial focuses on the implementation technique and it doesn't mean that this is the approach that will bring the best modeling results.

We will be using the following pacakges:

```python
# IMPORT PACKAGES
from sklearn.svm import SVC
from sklearn.datasets import load_iris

from sklearn.model_selection import GridSearchCV
from sklearn.pipeline import Pipeline, FeatureUnion

from sklearn.decomposition import PCA
from sklearn.feature_selection import SelectKBest
```

We load the data into X,y:

```python
iris = load_iris()

X, y = iris["data"], iris["target"]
```

Now, we will apply two different feature extraction techniques:

- PCA
- SelectKBest

```python
# This dataset is way too high-dimensional. Better do PCA:
pca = PCA(n_components=2)

# Maybe some of the original features were good, too?
selection = SelectKBest(k=3)
```

Now, we will combine these ouputs with `FeatureUnion`:

```python
# Build an transformer from PCA and Univariate selection:
combined_features = FeatureUnion([("pca", pca), ("univ_select", selection)])
```

We will create an object for classification now:

```python
# We will initialize the classifier
svm = SVC(kernel="linear")
```

Let's finalize the pipeline and apply grid search to tune the parameters properly:

```python
# create our pipeline from FeatureUnion 
pipeline = Pipeline([("features", combined_features), ("svm", svm)])

# set up our parameters grid
param_grid = {"features__pca__n_components": [1, 2, 3],
                  "features__univ_select__k": [1, 2, 3],
                  "svm__C":[0.1, 1, 10]}

# create a Grid Search object
grid_search = GridSearchCV(pipeline, param_grid, verbose=10, refit=True)    

# fit the model and tune parameters
grid_search.fit(X, y)
```

Finally, we can print the best combination of parameters:

```python
print(grid_search.best_params_)
```

We can see the Python object that contains the best combination of parameters we got using GridSearch.

## Conclusion

We have seen how we can combine two pipelines together using `FeatureUnion`. Using this method, we can apply different transformations on selected subsets of columns.