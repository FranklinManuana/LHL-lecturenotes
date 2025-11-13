Review ColumnTransformer with the article [**What is the Scikit-learn ColumnTransformer?**](https://www.freecodecamp.org/news/machine-learning-pipeline/#what-is-the-scikit-learn-columntransformer).

ColumnTransformer is a class provided by sklearn that allows you to apply different preprocessing or feature extraction techniques to different subsets of columns in a dataset. This is useful when you have a dataset with multiple types of data, such as both numerical and categorical columns, and you want to apply different processing techniques to each type of column.

ColumnTransformer works by specifying a list of transformers, where each transformer is applied to a specific subset of columns in the dataset. The subsets of columns are specified using either column indices or column names. Once the transformers are defined, the ColumnTransformer applies each transformer to the appropriate columns in the dataset, and concatenates the results together to form a single transformed dataset.

![](https://i.imgur.com/sJRkEix.png)

The ColumnTransformer class can be used in conjunction with a Pipeline to create a custom end-to-end pipeline that applies different preprocessing or feature extraction techniques to different subsets of columns in a dataset.

For example, if you have a dataset with both numerical and categorical columns, you could use ColumnTransformer to apply a StandardScaler to the numerical columns and a OneHotEncoder to the categorical columns, and then include the ColumnTransformer in a Pipeline along with a classifier.

```python
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.ensemble import RandomForestClassifier

preprocessor = ColumnTransformer(
    transformers=[
        ('num', StandardScaler(), ['numerical_feature_1', 'numerical_feature_2']),
        ('cat', OneHotEncoder(), ['categorical_feature'])
    ])

pipe = Pipeline([
    ('preprocessor', preprocessor),
    ('classifier', RandomForestClassifier())
])
```

In this example, the ColumnTransformer applies the StandardScaler to the numerical columns 'numerical_feature_1', 'numerical_feature_2' and OneHotEncoder to the categorical column 'categorical_feature'. The output of the ColumnTransformer is then passed as input to the next step in the pipeline which is a classifier.

Instruction

Follow the steps in the article [**How to Create a Pipeline**](https://www.freecodecamp.org/news/machine-learning-pipeline/#how-to-create-a-pipeline) to implement a pipeline and use ColumnTransformer