_Dimensionality Reduction_ is a process of reducing the number of random variables and creating a set of principal variables. We can use this concept to reduce the number of features in your dataset without having to lose much information.

You can split it into two parts: - Dimensionality reduction - Variable selection

![Dimensionality reduction techniques flowchart. Breaks into feature selection (missing value ratio, low variance filter, high correlation filter, random forest, backward feature extraction, forward feature selection). The other is dimensionality reduction, which breaks down into components/factors-based, and projection based. Components/factors involve Factor analysis, principal component analysis, independent component analysis. Projection-based is ISOMAP, t-SNE, and UMAP.](https://i.imgur.com/q9kkbvl.png)

Now you will cover the most important techniques from both parts.

## Why Is This Important?

Instruction

You can read about the motivation for _dimensionality reduction_ in the PDF copy of this Medium article [Why is Dimensionality Reduction so Important?](https://drive.google.com/file/d/1TPd7LuE5TKC0nlQx00kQS0AeNw2eM5gN/view?usp=drive_link) The author mentions overfitting as a classic example. We will cover it more deeply later in the program.

There are more cases where _dimensionality reduction_ can be useful. Some common scenarios are:

- _Visualization_ – because a projection into 2-3 dimensions can be plotted.
- _Reduction of time complexity_ – because less computation is required.
- _Reduction of space complexity_ – because of a lower number of features.
- _Better interpretability_ – because noise is reduced which allows for a simpler explanation.
- _Feature Extraction_
- _Anomaly Detection_, e.g. PCA subspace