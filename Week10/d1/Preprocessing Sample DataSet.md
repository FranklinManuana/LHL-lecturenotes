In the last reading, you were introduced to the basics of text data preprocessing techniques. You will now utilize those techniques and practice preprocessing a sample dataset.

## Movie Reviews Data Preprocessing

In this task, you will be given a dataset (`imdb_movie_reviews.csv`) focused on movie reviews. You will work on this dataset to:

1. Remove punctuation
2. Tokenize the text
3. Remove stop words

Instruction

**Download the Dataset**: Before you proceed, download the dataset (`imdb_movie_reviews.csv`) given [here](https://learningimages.lighthouselabs.ca/Data+BC/LLM/Unit_2/imdb_movie_reviews.csv) and load it into a pandas DataFrame.

#### Note

You will use this dataset to practise Removing punctuation, Tokenization and Stop word removal in this exercise. Let's begin by removing punctuation from the dataset.

### Removing Punctuation

**Step 1**: Review the possible punctuation.

```python
import string

string.punctuation

>>> '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
```

**Step 2**: Create a function that takes a review as an argument and returns a review with no punctuation.

```python
def remove_punctuation(review):
    # TODO: your code goes here

    return review
```

**Step 3**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toogle Answer_ button.

**Your Answer**

**Step 4**: Now that you have defined your function, call the function and pass a string of text with punctuation (and make sure you are happy with the results).

**Step 5**. Finally, create a new column in your DataFrame by applying this function to the review series.

```python
df['review_no_punct'] = df['review'].apply(lambda x: remove_punctuation(x))
```

You did it—your new column should now have reviews with all punctuation removed.

Next you will jump to the tokenization.

### Tokenization

You will now tokenize the movie reviews by creating a list of words from the reviews that have had punctuation removed. It is also customary to make sure that all letters are lowercase to reduce the size of the vocabulary due to differences in capitalization.

**Step 1**: Create a function that takes a review as an argument and returns a list of lowercase individual words.

```python
def tokenize(review):
    # TODO: your code goes here

    return tokens
```

**Step 2**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toggle Answer_ button.

**Your Answer**

Question

Ask Yourself: Does your function return a list of individual words? Did you remember to lowercase each word? Test it out and see.

**Step 3**: Using a lambda function, create a new column in your DataFrame with tokenized movie reviews from the reviews with no punctuation.

**Step 4**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toggle Answer_ button.

**Your Answer**

**Step 5**: Analyze what is the minimum, maximum, and average number of words in the tokenized reviews (hint: use the .apply(len) method on the series).

**Step 6**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toggle Answer_ button.

**Your Answer**

You have successfully tokenized the movie reviews. You will now remove the stop words next.

### Stop Word Removal

In this section, you will be removing stop words from the tokenized movie reviews. Stop words add little value to the meaning of the text in the context of NLP. To do this, you will need to use the NLTK. Explore the specific steps to remove stop words beginning with installing the toolkit.

**Step 1**: Install NLTK now if you have not already done so.

```python
pip install nltk
```

**Step 2**: Import the relevant module from nltk and choose English stopwords since this is the language the reviews are written in.

```python
from nltk.corpus import stopwords

stop_words = stopwords.words('english')
```

**Step 3**: Review the list stored in the stop_words variable.

Question

Observe the stop words: How many stop words are there? Can you see how these words can be removed while the general context of the sentence is still maintained?

**Step 4**: Define a function that removes stop words from the tokenized reviews.

```python
def remove_stopwords(review): 
    # TODO: your code goes here

    return review
```

**Step 5**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toggle Answer_ button.

**Your Answer**

**Step 6**: Just as you have done before, create a new column in your DataFrame with tokens with stop words removed.

**Step 7**: Toggle for the solution.

Question

Write your response in the space provided and then hit the _Toggle Answer_ button.

**Your Answer**

**Step 8**: Now compare the minimum, maximum, and average number of words from the tokenized reviews to the tokenized reviews with stop words removed.

Question

**Moment of Reflection**: What does this do for the dimensionality of your data considering that each word can be a feature?

## Develop a Report (optional)

After you have cleaned the dataset using both the techniques, develop a brief report describing your findings and observations.

Instruction

**Report Submission**: Develop your report in a notebook file (.ipynb). Once done, post your report on Discord for any peer feedback.

On Discord, you may discuss with your peers any learnings you had while working on this exercise, or any challenges you faced in completing the exercise.

Note

**Save Your Report for Portfolio**: You may also save your report for future reference, or for your professional portfolio.

## Additional Stretch Work

In case you want to do additional practice of text data preprocessing (removing punctuation, tokenizing text, and removing stop words), follow the steps in the article [How to Clean Text for Machine Learning with Python](https://machinelearningmastery.com/clean-text-machine-learning-python/) and run the code in your own Jupyter Notebook.

## Conclusion

This exercise helped solidify your understanding of tokenization and stop word removal. Next, you will jump to the lecture to get in-depth insights about LLMs and additional data preprocessing techniques.

## Reference

*_Dataset Source_: [Large Movie Review Dataset](https://ai.stanford.edu/%7Eamaas/data/sentiment/)

*_Dataset Citation_:

@InProceedings{maas-EtAl:2011:ACL-HLT2011, author = {Maas, Andrew L. and Daly, Raymond E. and Pham, Peter T. and Huang, Dan and Ng, Andrew Y. and Potts, Christopher}, title = {Learning Word Vectors for Sentiment Analysis}, booktitle = {Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies}, month = {June}, year = {2011}, address = {Portland, Oregon, USA}, publisher = {Association for Computational Linguistics}, pages = {142--150}, url = {[http://www.aclweb.org/anthology/P11-1015](http://www.aclweb.org/anthology/P11-1015)} }

_References_: Potts, Christopher. 2011. On the negativity of negation. In Nan Li and David Lutz, eds., Proceedings of Semantics and Linguistic Theory 20, 636-659.

_Contact_: For questions/comments/corrections, please contact Andrew Maas ([amaas@cs.stanford.edu](mailto:amaas@cs.stanford.edu))