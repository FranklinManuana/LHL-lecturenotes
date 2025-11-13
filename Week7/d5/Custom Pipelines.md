## Tutorial

We will cover two ways of customization:

- Putting our own classes into a pipeline.
- Using ColumnTransformer from `sklearn`.

Instruction

Follow the PDF copy of this Towards Data Science article called [Two Ways to Create Custom Transformers with Sci-kit Learn](https://drive.google.com/file/d/12NPGlBR8-jsZx390uwn1agHYSfX6Xw8h/view?usp=drive_link) to learn how to choose a subset of columns for some processing steps and how to implement own functions inside a pipeline.

## Conclusion

In the previous sections, we have seen what we can do with **Pipelines**:

- Tune parameters of **ALL** steps.
- Combine features from different pipelines using `FeatureUnion`.
- Select a subset of features for pipeline steps with ColumnTransformer.
- Create our own transformers and include them in a pipeline.