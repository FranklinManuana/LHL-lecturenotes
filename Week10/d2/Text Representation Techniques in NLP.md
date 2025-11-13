Previously, you learned about the basics of text data preprocessing techniques. In this reading (and in this unit), you will now learn the basics of text representation techniques in NLP.

## Reading

Text representation in NLP is a critical concept that involves converting text data into a format that can be understood and processed by computers. This transformation is essential because computers inherently do not understand human languages and need data to be in a structured and numeric form.

Different steps in the text representation process can be briefly described as follows:

![Text Preprocessing Steps](https://learningimages.lighthouselabs.ca/Data+BC/LLM/Unit_3/U3_A01_01.png)

_Fig 1_: Text Preprocessing Steps

- **Step 1 Input Text**: The process begins with raw text input. This can be anything from a sentence, to a paragraph, or to a document.
    
- **Step 2 Preprocessing**:
    

_Step 2A Cleaning_: Remove unnecessary elements like HTML tags, special characters, and numbers, depending on the context.

_Step 2B Normalization_: Convert text to a standard format, like lowercasing all letters and removing punctuation.

_Step 2C (Optional Steps)_: Depending on the requirement, this may include removing stop words (common words like 'the', 'is', 'in', which are often irrelevant in analysis) and stemming/lemmatization (reducing words to their base or root form).

- **Step 3 Tokenization**:

_Breaking Down Text_: Split the preprocessed text into tokens. Tokens are typically words, but can also be phrases, symbols, or other meaningful elements.

_Output_: A list of tokens.

Note

You will learn more about the tokenization process later in the course.

- **Step 4 Vectorization**: Here you convert tokens into numerical values. There are different methods to perform vectorization, as described below:

_BoW_: Represent the text by the frequency of each word. Each word in the vocabulary is assigned a unique index, and the frequency of the word in the text is noted in the corresponding index.

_TF-IDF_: Improve upon BoW by considering both the frequency of a word in a document and its inverse frequency across all documents.

_Multi-Hot Vectorization_: Multi-hot vectorization is a method used in NLP and ML to represent textual data, especially when dealing with sets of items like words, tags, or categories. It allows multiple elements in the vector to be hot (set to 1) at the same time. This is useful for representing a set of items, such as multiple words in a document or multiple tags associated with an article.

Note

**Python Examples**: Python examples of BoW and TF-IDF have been given later in the reading. Feel free to take a look, if you wish.

Note

**BoW vs. TF-IDF**: Do you wonder how BoW exactly differs from TF-IDF. Read [BOW vs TF-IDF for NLP Text Vectorization](https://www.linkedin.com/pulse/bow-vs-tf-idf-nlp-text-vectorization-hassan-badawy-msc/) to compare the two techniques.

_Word Embeddings_: Use models like Word2Vec, GloVe, or FastText to convert each token into a dense vector that captures semantic meanings.

External Resource

Read [The Illustrated Word2vec](https://jalammar.github.io/illustrated-word2vec/) to get an in-depth understanding of the Word2Vec model.

_Contextual Embeddings (Advanced)_: For more sophisticated applications, use models like BERT or GPT to generate vectors that consider the context of each word in the text.

External Resource

Read [A Guide on Word Embeddings in NLP](https://www.turing.com/kb/guide-on-word-embeddings-in-nlp) to learn more about vectorization techniques in NLP.

- **Step 5 Output Vectorized Text**:

_End Point_: The result is a numerical representation of the text, which can be used in various NLP applications like classification, sentiment analysis, etc.

Note

Based on specific requirements, there may be optional steps during the text conversion process, as mentioned below.

_Dimensionality Reduction_: Methods like PCA and LDA can be applied, especially in the case of high-dimensional vectors. PCA and LDA both attempt to reduce embeddings to single-dimensional vectors. Just be aware that this simplification of the vector space comes with a tradeoff for interpretability. Be cognisant of how important explainability is in your model before deploying production models including these techniques.

_Feature Selection_: Selecting the most relevant features (words/terms) for the task at hand.

This flow outlines the general process of converting raw text into a numerical form that can be processed by ML models in NLP. The exact steps and techniques used can vary based on the specific requirements of the task and the nature of the text data.

### BoW and TF-IDF Python Examples

Here are small Python examples demonstrating BoW and TF-IDF using `scikit-learn`:

Consider the following sample documents:

- "the quick brown fox jumped over the lazy dog"
- "the dog jumped over the quick fox"
- "quick brown fox"

The corpus contains eight unique words, namely “brown,” “dog,” “fox,” “jumped,” “lazy,” “over,” “quick,” and “the.” The below explains how these documents would be represented using BoW and TF-IDF.

### BoW

For BoW, each document is represented as a vector indicating the frequency of each word in the entire corpus (this is also known as _frequency encoding_).

||**Document 1**|**Document 2**|**Document 2**|
|---|---|---|---|
|brown|1|0|1|
|dog|1|1|0|
|fox|1|1|1|
|jumped|1|1|0|
|lazy|1|0|0|
|over|1|1|0|
|quick|1|1|1|
|the|2|2|0|

The corpus contains eight unique words, so each document is represented as an eight-dimensional vector. Using the table above, you can see that the BoW representation of the documents is as follows:

- Document 1: [1,1,1,1,1,1,1,2]
- Document 2: [0,1,1,1,0,1,1,2]
- Document 3: [1,0,1,0,,0,0,1,0]

BoW merely represents the frequency of words in a corpus. It does not take grammar, word order, context, or relative importance of a word into consideration.

### TF-IDF

TF-IDF, on the other hand, reflects how important a word is to a document in a collection. It not only considers the frequency of the word in the current document (term frequency), but also how rare the word is across all documents (inverse document frequency).

![Text Preprocessing Steps](https://learningimages.lighthouselabs.ca/Data+BC/LLM/Unit_3/U3_A01_02.jpg)

_Fig 2_: TF-IDF

|||**Document 1**|**Document 1**|**Document 2**|**Document 2**|**Document 3**|**Document 3**|
|---|---|---|---|---|---|---|---|
|**Term**|**IDF**|**TF**|**TF*IDF**|**TF**|**TF*IDF**|**TF**|**TF*IDF**|
|brown|log(3/2)|1/9|0.0196|0/7|0|1/3|0.1590|
|dog|log(3/2)|1/9|0.0196|1/7|0.0252|0/3|0|
|fox|log(3/3)|1/9|0|1/7|0|1/3|0|
|jumped|log(3/2)|1/9|0.0196|1/7|0.0252|0/3|0|
|lazy|log(3/1)|1/9|0.0530|0/7|0|0/3|0|
|over|log(3/2)|1/9|0.0196|1/7|0.0252|0/3|0|
|quick|log(3/3)|1/9|0|1/7|0|1/3|0|
|the|log(3/2)|2/9|0.0391|2/7|0.0503|0/3|0|

The TF-IDF representation is as follows:

- Document 1: [0.0196, 0.0196, 0, 0.0196, 0.0530, 0.0196, 0, 0.0391]
- Document 2: [0, 0.0252, 0, 0.0252, 0, 0.0252, 0, 0.0503]
- Document 3: [0.1590, 0, 0, 0, 0, 0, 0]

Note

Scikit learn uses a slightly modified equation to calculate TF-IDF so you will notice the IDF values from the example and the code will not match precisely.

In both methods, the words are tokenized, and each column of the arrays corresponds to a unique word in the corpus. The difference lies in how the importance of each word is calculated.

Note

_Here is the code_:

```python
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer

# Example documents
documents = [
    "the quick brown fox jumped over the lazy dog",
    "the dog jumped over the quick fox",
    "quick brown fox"
]

# Bag of Words (BoW)
bow_vectorizer = CountVectorizer()
bow = bow_vectorizer.fit_transform(documents)
bow_array = bow.toarray()

# Term Frequency-Inverse Document Frequency (TF-IDF)
tfidf_vectorizer = TfidfVectorizer()
tfidf = tfidf_vectorizer.fit_transform(documents)
tfidf_array = tfidf.toarray()

bow_array, tfidf_array

```

Warning

_scikit-learn_ uses a smoothed _TF-IDF_ formula and normalizes the resulting vectors. Thus, if you try to calculate using the formula given here, you may not get the same results.

Note

_Here is the result_:

## Further Reading

1. [Evolution of Natural Language Processing](https://www.freshgravity.com/evolution-of-natural-language-processing/)
2. [What is Tokenization in NLP? Here’s All You Need To Know](https://www.analyticsvidhya.com/blog/2020/05/what-is-tokenization-nlp/)