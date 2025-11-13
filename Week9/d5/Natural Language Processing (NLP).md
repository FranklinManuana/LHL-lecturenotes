In this activity, we will discuss Natural Language Processing (NLP).

We'll focus on two important techniques:

1. LDA (Latent Dirichlet Allocation)
2. NMF (Non-Negative Matrix Factorization) for topic modeling

Note

These skills are valuable for text analysis and recommendation systems.

Throughout the activity, you'll use Python and Sklearn, a popular library for machine learning. Plus, you'll see how AI can save you time by automating repetitive tasks.

## Learning Outcomes

- Generate bite-size blocks of code so that you can see how different steps fit together
- Deepen your understanding of NLP and LDA/topic modelling
- Practice using AI for redundant tasks

Instruction

Use ChatGPT to answer the following questions before (or while) you perform the next tasks.

Answering these questions should help you complete the rest of this assignment!

- What is the `tfidfvectorizer`?
- How is `tfidf` calculated?
- How does the `countvectorizer` differ from the `tfidfvectorizer`?
- How can I instantiate a `TfidfVectorizer` with the following parameters:
    - max_df = 0.95
    - min_df = 2
    - max_features = no_features
    - stop_words = 'english'
- What are the methods of the `tfidfvectorizer` object?
- What is NMF?
- What is LDA?

```python
# import TfidfVectorizer and CountVectorizer from sklearn
from Sklearn.feature_extraction.text import TfidfVectorizer, CountVectorizer

# import fetch_20newsgroups from sklearn.datasets
from sklearn.datasets import fetch_20newsgroups

# import NMF and LatentDirichletAllocation from sklearn
from sklearn.decomposition import NMF, LatentDirichletAllocation

dataset = fetch_20newsgroups(shuffle=True, random_state=1, remove=('headers', 'footers', 'quotes'))
documents = dataset.data
```

Instruction

Create a variable called `no_features` and set its value to 100.

Then, create a variable `no_topics` and set its value to 100.

## NMF

Instruction

Instantiate a `TfidfVectorizer` with the following parameters:

- max_df = 0.95
- min_df = 2
- max_features = no_features
- stop_words = 'english'

Instruction

Then, use the `fit_transform` method of `TfidfVectorizer` to transform the documents.

Instruction

Next, get the features names from `TfidfVectorizer`.

Instruction

Finally, instantiate NMF and `fit_transform` data.

## LDA with Sklearn

Instruction

Instantiate a `CountVectorizer` with the following parameters:

- max_df = 0.95
- min_df = 2
- max_features = no_features
- stop_words = 'english'

Instruction

Then, use the `fit_transform` method of `CountVectorizer` to transform documents.

Instruction

Next, get the features names from `CountVectorizer`.

Instruction

Next, instantiate `LatentDirichletAllocation` and fit transformed data.

Instruction

Finally, create a function `display_topics` that is able to display the top words in a topic for different models.

The expect outputs include:

- Display the top 10 words from each topic from NMF model
- Display the top 10 words from each topic from LDA model

#### Looking for an extra challenge? (Optional)

Instruction

Stretch: Use LDA with Gensim to complete all of the tasks in this exercise.

## Conclusion

You've explored NLP and mastered topic modelling using NMF and LDA. You've learned how to use Python's Sklearn library to work with text data efficiently. Plus, you've seen how AI can assist you in automating tasks.