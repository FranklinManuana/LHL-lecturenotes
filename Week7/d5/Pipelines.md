## What are `Pipelines?`

`Pipelines` can be used to chain multiple estimators (sklearn data processing and modeling steps) into one. This is useful as there is often a fixed sequence of steps in processing the data – for example: feature selection, normalization, and classification. Pipelines serve multiple purposes here:

- **Convenience and encapsulation -** You only have to call 'fit' and 'predict' once on your data to fit a whole sequence of estimators.
    
- **Joint parameter selection -** You can do a grid search over the parameters of all estimators in the pipeline at once.
    

All objects in a pipeline, except for the last one, must be transformers (i.e. must have a `.transform()` method). The last estimator may be any type (transformer, regressor or classifier).