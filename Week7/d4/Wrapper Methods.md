## Wrapper Methods

_Wrapper methods_ consider the selection of a set of features as a search problem, where different combinations are prepared, evaluated, and compared to other combinations. A predictive model is used to evaluate a combination of features and assign a score based on model accuracy.

The wrapper method techniques use a ML model to evaluate the performance of different subsets of features and select the subset that provides the best performance. Examples of wrapper methods include forward selection, backward elimination, and recursive feature elimination.

This is what the flow of the process of evaluating features and assigning scores based on model accuracy looks like:

![Process of selecting the best subset. Set of all features generate a subset then influence the elarning algorihm, which then generates a subset. This cycle continues. Evenetually, this results in performance.](https://i.imgur.com/XwtNhxT.png)

Some of the most popular examples of _wrapper methods_ are:

- Forward selection
- Backward elimination
- Stepwise selection

#### Forward Selection

It is an iterative method in which we keep adding a feature that best improves our model until the addition of a new feature does not improve the model performance.

![Forward selection when the feature set of Gi is {} and accuracy with Gi is 50%. {Xi} is 50%, {X2} is 51%, and so on until {X7} which is 68%, and continue to any {Xn} where it is 62%. From {X7}, {X7,X1} is 72% and {X7,X2} is 68%, continuing onto {X7, Xn}, which is 69%.](https://i.imgur.com/Wr7oKzv.png)

#### Backward Elimination

In this method, we start with all features and remove the least significant feature at each iteration which improves the model performance. We repeat this until no improvement is observed upon the removal of features.

![Backward elimination where X={X1....Xn} is 68%, which makes into X-{X1} at 65%, X-{X2} is 71%, continuing onto X-{X9} at 79%, and continuing onto X-{Xn} at 62%. X-{X9} breaks into X-{X9,X1} is 67%, and X-{X9,X2} is 74%, and continuing onto X-{X9, Xn} at 72%.](https://i.imgur.com/WsMgPLX.png)

Both of the methods above use a hill-climbing search.

#### Pros and Cons of Forward Selection and Backward Elimination

##### Forward Selection:

- Efficient for choosing a small subset of features.
- Misses features whose usefulness requires other features (feature synergy).

##### Backward Elimination:

- Efficient for discarding a small subset of features.
- Preserves features whose usefulness requires other features.
- Less efficient for computation. It takes more time to fit models with all features than with one feature. This will depend on the size and complexity of the data and the computational resources available.

#### Stepwise Selection

This type is a combination of the previous two. You start with 1 variable and keep adding a feature that best improves the model. In each step, you check the features you have already selected if the removal of one of those features won't improve the model.

Now we know all that you need to know to be able to practice the feature selection techniques.

---