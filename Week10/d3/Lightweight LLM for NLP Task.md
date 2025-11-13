## Introduction

Previously, you learned the basics of how pre-trained models are used to perform an NLP task. In this exercise, you will use the transformers module to use DistilBERT (a lightweight version of BERT) to perform various NLP tasks.

## Instructions

### Tokenization Exercise

Run the following code to tokenize the given sentence: _Tokenize this sentence using DistilBERT_.

```python

from transformers import DistilBertTokenizer

# Load the DistilBERT tokenizer
tokenizer = DistilBertTokenizer.from_pretrained('distilbert-base-uncased')

# Example sentence
sentence = 'Tokenize this sentence using DistilBERT.'

# Tokenize the sentence
tokens = tokenizer(sentence, return_tensors='pt')

# Retrieve the input_ids
input_ids = tokens['input_ids'].squeeze().tolist()

# Retrieve the attention mask
attention_mask = tokens['attention_mask'].squeeze().tolist()

# Print the results
print(f'Original sentence:\n{sentence}\n')
print(f'Input IDs:\n{input_ids}\n')
print(f'Attention mask:\n{attention_mask}')


>>> Original sentence:
Tokenize this sentence using DistilBERT.

Input IDs:
[101, 19204, 4697, 2023, 6251, 2478, 4487, 16643, 23373, 1012, 102]

Attention mask:
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]

```

Question

**Opportunity to Reflect**: The original sentence has only five words. Why are there 11 tokens?

Instruction

Map each input id to its corresponding token, as shown below.

```python

for input_id in input_ids:
      print(f'{input_id}: {tokenizer.decode([input_id])}')

>>> 101: [CLS]
19204: token
4697: ##ize
2023: this
6251: sentence
2478: using
4487: di
16643: ##sti
23373: ##lbert
1012: .
102: [SEP]

```

Note

Some important things to note about the process are:

- DistilBERT introduces the [CLS] and [SEP] tokens at the beginning and ending of a sentence, respectively.
- The tokenizer does not remove punctuation as part of the preprocessing step.
- Words that have been lemmatized are prefixed with ##.

This further goes to show why it is crucial to use the tokenizer specific to the model you are using.

Instruction

Now try to assess the tokens of some additional sample sentences as you did in the example above.

Question

**Opportunity to Reflect** (optional): Once you are done assessing the sample sentences, reflect on the following prompts. You are encouraged to share your findings with your peers on Discord.

- What happens when you have a word that does not appear in the vocabulary?
    
    - Hint: include a nonsensical word or an emoji in your test sentence.
- What is the usefulness of this special token?
    
- Are there any challenges or considerations regarding this token?
    

## Conclusion

The Transformers module makes it very easy to abstract away much of the complexity of using pre-trained LLMs. You should already be using this module in your final project. Be sure to refer to the documentation often.