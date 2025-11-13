This section will explain how **centroid-based clustering** works. As a representative of this group of models, we have chosen the famous `k-means` algorithm.

## K-means

In _centroid-based clustering_, clusters are represented by a central vector, which may not necessarily be a member of the dataset. When the number of clusters is fixed to `k`, `k-means` clustering gives a formal definition as an optimization problem: find the `k` cluster centers and assign the objects to the nearest cluster center such that the squared distances from the cluster are minimized.

Squared distances are used in k-means clustering instead of simply using the absolute distances for a few reasons:

- Squared distances are more interpretable
- Squared distances eliminate the need for absolute values
- Squared distances penalize larger deviations more
- Squared distances simplify the optimization problem

Instruction

Watch the video below to understand how `k-means` works:

Note

If the variables in the data are on a different scale (for example, Age and Income of people), we need to scale these columns to be on the same scale. If we fail to do that, one variable will have much bigger impact to our model than the other one.

### Scaling Data

Common techniques for this problem are normalization and standardization :

#### Normalization

This is the process of rescaling numeric values in the dataset to a common scale, typically between 0 and 1 or -1 and 1, without distorting the original distribution. This is often done to ensure that different features or variables in the dataset are comparable and have equal influence on the analysis. For example, if a dataset has variables with different units of measurement, such as height in meters and weight in kilograms, normalization can help to standardize the variables and eliminate any bias towards variables with larger values.

#### Standardization

Standardization, on the other hand, is the process of transforming data to have zero mean and unit variance, usually by subtracting the mean and dividing by the standard deviation. This technique is used when the distribution of the data is not necessarily Gaussian or when the range of the data is not known in advance. Standardization is often used in machine learning algorithms, such as linear regression and logistic regression, to improve convergence and performance by reducing the effects of outliers and extreme values in the dataset.

## Summary

Instruction

You can review the PDF copy of this Towards Data Science article for a short and clear summary of [`k-means` clustering](https://drive.google.com/file/d/1EmV7E4QCAudoQUR8nciK8KIt5aQjIlxT/view?usp=drive_link).