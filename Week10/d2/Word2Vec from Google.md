You learned the basics of Word2Vec vectorization technique in the reading _Text Representation Techniques in NLP_. In this activity, you will see how to use pre-trained Word2Vec models from the internet.

## Pre-Trained Word2Vec Model from Google

One of the most famous pre-trained Word2Vec models that can be found online is the one from Google. You will see how you can download and use it to find interesting relationships between various words.

Instruction

You can find more information about the model in the article [Word2Vec Implementation using Python Gensim and Google Colab](https://datamahadev.com/word2vec-implementation-using-python-gensim-and-google-colab/).

Once you have the model loaded in Python, you can play with its different methods and attributes. Firstly, you can find the numeric vector for every word (it will always have a length of 300).

```python
vector = model['easy']
# see the shape of the vector (300,)
vector.shape
```

### Similarities

You can find the most similar words to any word:

```python
model.most_similar("nice")
```

Or a similarity score of any two words:

```python
model.similarity("nice","good")
```

Interestingly, if you take two antonyms (words with opposite meaning), they are going to be highly similar according to a good Word2Vec model. This is because you can usually replace opposite words with each other in the text.

```python
# Interesting
model.similarity("bad","good")
```

You can also look for interesting relationships between words.

```python
# king - queen = man - woman
model.most_similar(positive=['woman', 'king'], negative=['man'])
```

Now try it on your own.

Instruction

Using the logic from the previous example, `king - queen = man - woman` and the `most_similar` function from Word2Vec model, replace the `?` in the following lines:

- mom - girl = dad - ?
- france - paris = spain - ?
- mother - ? = table - chair

This library looks quite powerful, right?

Note

Create Your Own Word2Vec Model: In the upcoming lecture, your instructor will demonstrate how to build your own Word2vec model so that you don't have to rely on Google every time.

---