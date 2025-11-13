## Deploying ML using Flask

## Part I: Model Creation

Note

This tutorial focuses on the implementation technique and it doesn't mean that this is the approach that will bring the best modeling results.

Let's start with the import of packages we are going to need.

```python
import pandas as pd
from sklearn.datasets import load_wine

from sklearn.model_selection import GridSearchCV
from sklearn.pipeline import Pipeline, FeatureUnion

from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.feature_selection import SelectKBest

from sklearn.ensemble import RandomForestClassifier

import pickle
```

We will load the toy dataset directly from `sklearn`.

```python
data = load_wine()
df = pd.DataFrame(data['data'])
df.columns = data['feature_names']
y = data['target']
df.head()
```

During the model creation, we will work on following tasks:

- Filter own columns for PCA
- Scaling
- PCA
- SelectKBest
- Random Forest Regressor

and put them all to one pipeline.

### Filter Own Columns

Firstly, we will create our own class to keep only features we want in our pipeline. We don't want to run PCA on all features but only on the sample so we create our own class that filters the features in the original dataframe. We can put our own classes into the pipelines, as long as they have following methods:

- .fit()
- .transform()
- .fit_transform()

```python
# own class that can be inserted to pipeline as any other sklearn object.
class RawFeats:
    def __init__(self, feats):
        self.feats = feats

    def fit(self, X, y=None):
        pass


    def transform(self, X, y=None):
        return X[self.feats]

    def fit_transform(self, X, y=None):
        self.fit(X)
        return self.transform(X)


# features we want to keep for PCA
feats = ['alcohol','malic_acid','ash','alcalinity_of_ash','magnesium',
         'total_phenols','flavanoids','nonflavanoid_phenols']
# creating class object with indexes we want to keep.
raw_feats = RawFeats(feats)
```

### Scaling and PCA

```python
sc = StandardScaler()
pca = PCA(n_components=2)
```

### SelectKBest

```python
selection = SelectKBest(k=4)
```

### Random Forest

```python
rf = RandomForestClassifier()
```

### Combining Everything Into One Pipeline

As in the [previous tutorial](https://web.compass.lighthouselabs.ca/fbed35e1-4390-4dee-9c5d-70e68cd614c3) we will apply two different feature extraction techniques:

- PCA
- SelectKBest

and combine them with `FeatureUnion`. The small difference is that we will use only sample of features for PCA.

```python
PCA_pipeline = Pipeline([
    ("rawFeats", raw_feats),
    ("scaler", sc),
    ("pca", pca)
])

kbest_pipeline = Pipeline([("kBest", selection)])
```

Now, we will combine these ouputs with `FeatureUnion`:

```python
all_features = FeatureUnion([
    ("pcaPipeline", PCA_pipeline), 
    ("kBestPipeline", kbest_pipeline)
])
```

Now, we will create the **main** pipeline which ends with _Regressor_.

```python
main_pipeline = Pipeline([
    ("features", all_features),
    ("rf", rf)
])
```

Let's apply grid search to tune the parameters properly:

```python
# set up our parameters grid
param_grid = {"features__pcaPipeline__pca__n_components": [1, 2, 3],
                  "features__kBestPipeline__kBest__k": [1, 2, 3],
                  "rf__n_estimators":[2, 5, 10],
                  "rf__max_depth":[2, 4, 6]
             }

# create a Grid Search object
grid_search = GridSearchCV(main_pipeline, param_grid, n_jobs = -1, verbose=10, refit=True)    

# fit the model and tune parameters
grid_search.fit(df, y)
```

We were able to call the pipeline on the original dataset without any transformations. We can check the best combination of parameters:

```python
print(grid_search.best_params_)
```

We will use pickle to store the model onto our disk.

```python
pickle.dump( grid_search, open( "model.p", "wb" ) )
```

## Part II: API Creation

Now we go back to flask. Our goal is to build an API that will classify wine into the class when it receives the information about it.

Note

We don't have to retrain the model in the cloud. We will use the pickle file from the model which was developed on our local machines.

In a new file (we can call it `api.py` and store it in the same directory like our previous notebook and pickle file `model.p`), let's begin by importing the necessary libraries we'll need:

```python
# import Flask and jsonify
from flask import Flask, jsonify, request
# import Resource, Api and reqparser
from flask_restful import Resource, Api, reqparse
import pandas as pd
import numpy
import pickle
```

Warning

This should be the `.py` Python file, not `.ipynb`.

Create an API similar to previous [tutorial](https://web.compass.lighthouselabs.ca/423e4b9f-73f0-4aee-a4fe-52ba94c6acbf).

```python
app = Flask(__name__)
api = Api(app)
```

At the beginning of the file, we need to create the same custom class we used in the model creation part. The functions from that class are used in the model and stored in the pickle file we created earlier. Therefore, the model needs to have access to the class during the scoring as well. The accesses to other `sklearn` modules are provided automatically and we don't have to do anything about them in the scoring file.

```python
class RawFeats:
    def __init__(self, feats):
        self.feats = feats

    def fit(self, X, y=None):
        pass


    def transform(self, X, y=None):
        return X[self.feats]

    def fit_transform(self, X, y=None):
        self.fit(X)
        return self.transform(X)
```

Now, we will load our model (from pickle).

```python
model = pickle.load( open( "model.p", "rb" ) )
```

Now, we need to create an endpoint where we can communicate with our ML model. This time, we are going to use `POST` request.

```python
class Scoring(Resource):
    def post(self):
        json_data = request.get_json()
        df = pd.DataFrame(json_data.values(), index=json_data.keys()).transpose()
        # getting predictions from our model.
        # it is much simpler because we used pipelines during development
        res = model.predict_proba(df)
        # we cannot send numpt array as a result
        return res.tolist() 
```

Now, we need to assign an endpoint to our API.

```python
# assign endpoint
api.add_resource(Scoring, '/scoring')
```

The last thing to do is to create an application run when the file `api.py` is run directly (not imported as a module from another script).

```python
if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5000)
```

Now that we've created our API, it's time to test it.

Instruction

Run the API by opening the command line and type `python api.py`.

If there's no problem with our code, we will see the following in the command line:

```bash
 * Serving Flask app "api" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 471-591-853
```

We can see that our API is running on our local machine at `http://127.0.0.1:5000/`.

To test it, we need to send the information about wine in JSON to the endpoint: `http://127.0.0.1:5000/scoring`. We can now go back to Jupyter Notebook.

This is the structure of the JSON we need to send (values are from the first row of `df` in the original notebook where we created the model):

```python
json_data = {'alcohol': 14.23,
 'malic_acid': 1.71,
 'ash': 2.43,
 'alcalinity_of_ash': 15.6,
 'magnesium': 127.0,
 'total_phenols': 2.8,
 'flavanoids': 3.06,
 'nonflavanoid_phenols': 0.28,
 'proanthocyanins': 2.29,
 'color_intensity': 5.64,
 'hue': 1.04,
 'od280/od315_of_diluted_wines': 3.92,
 'proline': 1065.0}
```

Now, we can send our `POST` request from jupyter notebook:

```python
import requests
URL = "http://127.0.0.1:5000/scoring"
# sending get request and saving the response as response object 
r = requests.post(url = URL, json = json_data) 
```

and we can check results with:

```python
print(r.json())
```

It should be something like: `[[1.0, 0.0, 0.0]]` where each value is probability of being in that particular class. We can test it by using Postman APP as well.

## Conclusion

In this tutorial, we have deployed our first ML model. Now, we will go back to simpler Flask App and try to make it work in the cloud. During the mini-project, we will combine these skills, create a new ML model and deploy it to the cloud.