You learned the basics of text representations in the reading _Text Representation Techniques in NLP_. In this walkthrough, you will focus on numerical representations of text.

In this tutorial, you'll explore how to process text data for effective feature extraction in ML models. The key is converting text data into numerical vectors. You will now delve into various methods for achieving this.

### BoW Model

Start by extracting a unique set of words (vocabulary) from a collection of documents.

Each document is then represented as a vector. Each vector element corresponds to a word in the vocabulary—with a '1' if the word is present in the document and '0' otherwise (this is also known as _multi-hot encoding_).

Example:

```python
documents = ["LOVE THIS PHONE", "DISLIKE THIS PHONE"]
vocabulary = set(word.lower() for doc in documents for word in doc.split())
vectors = [[1 if word in doc.lower().split() else 0 for word in vocabulary] for doc in documents]
print("Vocabulary:", vocabulary)
print("Vectors:", vectors)
```

### Word Counts with CountVectorizer (scikit-learn)

Utilize CountVectorizer to create a vocabulary from the documents and count the occurrences of each word.

Example:

```python
from sklearn.feature_extraction.text import CountVectorizer
documents = ['LOVE THIS PHONE', 'DISLIKE THIS PHONE']
vectorizer = CountVectorizer()
vectorizer.fit(documents)
print('Vocabulary:', vectorizer.vocabulary_)
vector = vectorizer.transform(documents)
print('Vectors:', vector.toarray())
```

### Word Frequencies with TfidfVectorizer (scikit-learn)

TF-IDF is used to weigh the frequency of words, emphasizing words that are unique to certain documents.

Example:

```python
from sklearn.feature_extraction.text import TfidfVectorizer
documents = ["LOVE THIS PHONE", "DISLIKE THIS PHONE"]
vectorizer = TfidfVectorizer()
vectorizer.fit(documents)
print('Vocabulary:', vectorizer.vocabulary_)
print('IDF Values:', vectorizer.idf_)
vector = vectorizer.transform([documents[0]])
print('Vector:', vector.toarray())
```

### Analysis

![Equation for calculating TF-IDF](https://learningimages.s3.amazonaws.com/Data%20BC/LLM/Unit_2/equation_for_calculating_tfdf.jpg)

Finally, the vectors are scaled using 'l2' normalization so that the sum of the squares of each of the document vectors always equals one.

## Conclusion

Among the three methods, TF-IDF is often preferred because it effectively downplays common words (like 'this') that appear in multiple documents, focusing instead on words that are more unique to each document.

With these steps, your text data is now ready for use in ML models. So, in this walkthrough, you solidified your understanding of vectorization techniques.