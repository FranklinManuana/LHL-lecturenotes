### Introduction

Earlier in the course, you performed some preprocessing to text in your datasets.

When using a pre-trained model, the way you preprocess your text should be identical to the way the text was preprocessed when the model was trained. This ensures that the model receives the correct input to be able to successfully make inferences about new data. Hugging Face Transformers abstracts much of the code you would need to do this for your specific model you have chosen.

## Reading

### Tokenization

The main class you need to perform preprocessing is the Tokenizer class. The Tokenizer will:

- Convert the text into numerical representations
- Add special tokens to indicate the beginning and end of sentences (CLS and SEP):
    - Not all models require these tokens; BERT is an example of a model that does
    - The custom Tokenizer will automatically include these depending on the model selected
- Assemble the tokens into tensors required as inputs for the deep learning framework of your choice
- Provide any additional information required for your model such as attention masks, etc.

Warning

When you use a pre-trained model, you MUST use the Tokenizer specific to your model.

Using the Tokenizer specific to your model does all the preprocessing that was used on the corpus during training. This also maintains the correct indexing for each word in the model’s vocabulary.

### Sentence Length

After text is tokenized and transformed into tensors, they must be the same length as model inputs must be uniform. To ensure that all sentences are the same length, you may need to **_pad_** or* **truncate*** each of the sentences.

Note

**Padding** is a process where you can add zeros to act as a placeholder so that a short sentence will be the same length as the longest sentence in the corpus.

Note

**Truncation** is a process where a long sentence is chopped to meet the same length criteria. It is usually good practice to find out the maximum length of all the sentences in the corpus and use this to ensure all vocabulary is captured by your model.

External Resource

**Read Transformers Documentation**: For more reference on how these steps can be applied, please refer to the [Transformers documentation](https://huggingface.co/docs/transformers/preprocessing). You will get more hands-on experience in the next exercise.

## Conclusion

Next, you will apply a lightweight LLM to perform a basic NLP task.