In the previous exercise _Preprocessing Sample Dataset_, you worked towards cleaning the Movie Reviews dataset using punctuation removal, tokenization, and stop word removal techniques. In this exercise, you will now continue where you left off and apply stemming and lemmatization that you learned about in the lecture.

### _Movie Reviews_ Data Preprocessing Continues

In this exercise, you will practice stemming (reducing words to their root form) and lemmatization (reducing words to their base or dictionary form).

Instruction

**Use the Movie Reviews Dataset**: In this task, you will use the same dataset (_imdb_movie_reviews.csv_) that you previously used in the _Preprocessing Sample Dataset_ exercise.

### Stemming

Instruction

Follow the instructions given here to continue preprocessing the Movie Reviews dataset using the stemming technique.

**Step 1**: Use the tokenized text (without stop words) from the previous exercise (_Preprocessing Sample Dataset_).

**Step 2**: Import the necessary modules from NLTK:

```python
import nltk
nltk.download('punkt')
from nltk.stem import PorterStemmer
```

**Step 3**: Write a script to apply stemming to these tokens. You will do this by first instantiating an object of the `PorterStemmer` class and assigning it to a variable.

**Step 4**: Invoke the `.stem` method of your PorterStemmer object on several samples of the tokenized text with stop words removed from the previous exercise.

**Step 5**: Display the output and observe the changes in word forms.

Note

PorterStemmer is just one example of a stemming algorithm. To find more examples of other stemmers, refer to the [NLTK Documentation](https://www.nltk.org/api/nltk.stem.html) on the stem module.

### Lemmatization

Instruction

Follow the instructions given here to continue preprocessing the Movie Reviews dataset using the “lemmatization” technique.

**Step 1**: As always, start by importing the appropriate modules.

```python
nltk.download('wordnet')
from nltk.stem import WordNetLemmatizer
```

**Step 2**: Instantiate a WordNetLemmatizer object and invoke the .lemmatize method. You will see that this method takes two keyword arguments.

```python
lemmatize(word, pos)
```

Loop through each word in the same text from the stemming section and pass them to the `word` argument. Select different parts of speech and pass them to the `pos` argument. This argument defaults to `n` (nouns). Other valid options are:

- `v` (verbs)
- `a` (adjectives)
- `r` (adverbs)
- `s` (satellite adjectives).

**Step 3**: Compare the results of stemming and lemmatization on the same text.

> ##### **Reflection Opportunity**: Now that you have used both preprocessing techniques, reflect on the prompts given below.

- Effect of stemming and lemmatization on text processing and understanding
- Discuss scenarios where one method might be preferred over the other
- Limitations and advantages of each method

### Develop a Report (optional)

After you have preprocessed the dataset using both the techniques and reflected on the process, develop a brief report describing your findings and observations.

Instruction

**Report Submission**: Develop your report on a notebook file (.ipynb). Once done, post your report on Discord for any peer feedback.

On Discord, you may discuss with your peers any learnings you had while working on this exercise, or any challenges you faced in completing the exercise.

Note

**Save Your Report for Portfolio**: You may also save your report for future reference, or for your professional portfolio.

## Additional Stretch Work

Want to stretch yourself a bit and further practice the newly learned text preprocessing skills? If yes, do the following:

Instruction

Clone [this](https://github.com/lighthouse-labs/NLP_exercise) repository and follow the instructions in the `NLP_data_preparation_exercise notebook`.

Note

**Reach out on Discord**: You are highly encouraged to reach out to your peers on Discord if you wish to share any information, challenges, or insight while performing the stretch exercise.

## Conclusion

Now that you have practiced and solidified your understanding of text data preprocessing, let's learn about pre-trained models in the upcoming reading.

---
