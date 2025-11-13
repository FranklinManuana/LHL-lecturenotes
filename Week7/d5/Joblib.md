In this reading, we will learn about another library used for object serialization called `joblib`.

## When to Use `Joblib`?

In the specific case of `Sklearn`, it may be better to use `joblib`’s substitute of `pickle` (dump & load), which is more efficient on objects that carry large `numpy` arrays internally, which is often the case for fitted `Sklearn` estimators.

Instruction

Read about `joblib` serialization in the article [**Persistence**](https://joblib.readthedocs.io/en/latest/persistence.html).