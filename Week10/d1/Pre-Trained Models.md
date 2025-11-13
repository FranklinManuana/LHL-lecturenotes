In this reading, you will learn what it means to pre-train a language model and how this pre-training is performed.

## Reading

### Understanding Pre-Trained Models

In the context of LLMs, a pre-trained model refers to a model that has already been trained on a large dataset before being fine-tuned or used for specific tasks. Pre-trained models are widely used in various domains such as NLP, computer vision, speech recognition, etc. Some of the popular pre-train models in the NLP domain are:

- **BERT** (Bidirectional Encoder Representations from Transformers): Developed by Google, it is designed to understand the context of a word in search queries.
    
- **GPT**: OpenAI’s models like GPT-2 and GPT-3 are designed for a variety of tasks such as translation, question answering, and text generation.
    
- **RoBERTa** (A Robustly Optimized BERT Pretraining Approach): It is a modified version of BERT that is trained with more data and for a longer time.
    
- **ALBERT** (A Lite BERT): Has fewer parameters than BERT, making it more efficient.
    
- **DistilBERT**: A smaller, faster, cheaper, and lighter version of BERT.
    

Note

You will learn more about DistilBERT later in the course.

Question

Did you know, not every pre-trained model is an LLM? Read on to understand how a pre-trained model is different from an LLM.

**Pre-Trained Model**: A pre-trained model is a broad term that refers to any ML model that has been previously trained on a dataset before it is deployed for use in specific tasks. These models are designed to be adapted or fine-tuned for various tasks with additional training, saving time and resources since they do not have to be trained from scratch.

**LLM**: An LLM, like GPT, is a specific type of pre-trained model that focuses on understanding and generating human language. It is trained on vast amounts of text data and can perform a wide range of language-related tasks, such as translation, question answering, and text generation.

**Pre-Trained Model vs. LLM**: In essence, all LLMs are pre-trained models, but not all pre-trained models are LLMs. Pre-trained models could also include image recognition systems, voice recognition systems, or any other type of ML model that has been trained on a dataset before being fine-tuned or used for inference on specific tasks.

### Pre-Training Process

Pre-training involves learning from a vast corpus of text data, which allows the model to understand and generate human-like text. Here's a brief overview of the pre-training process:

**Data Collection**: The model is exposed to a massive dataset, which can be a mix of books, articles, websites, and other text sources. This dataset is designed to cover a wide range of human knowledge and language use.

**Unsupervised Learning**: The pre-training is usually done in an unsupervised manner, meaning that the model learns patterns, associations, and structures in the data without explicit instructions on what it's supposed to learn. For example, it learns to predict the next word in a sentence, which helps it to grasp grammar, idioms, facts about the world, and even styles of writing.

**Learning Representation**: During pre-training, the model learns a numerical representation of language (word embeddings and contextual embeddings), which captures the essence of words and their meanings in different contexts.

**Generative Pre-Training**: For models like GPT, the pre-training involves a generative task where the model tries to predict the next word given the previous words in a sentence or passage (also known as language modelling). This task encourages the model to understand context and improve its language generation capabilities.

**Transformer Architecture**: LLMs like GPT utilize the transformer architecture, which allows them to process words in relation to all other words in a sentence, rather than one at a time in sequence. This gives the model a more nuanced understanding of language.

Note

**Pre-training followed by fine-tuning**: After the pre-training phase, the model can be fine-tuned on specific tasks (like translation, question answering, summarization, etc.) with smaller, task-specific datasets. Fine-tuning allows the model to adapt the general language abilities it has learned during pre-training to particular applications or domains of interest.

Pre-trained models are valuable (as the vast majority of users would not have the money/time/resources to train such a model from scratch) because they significantly reduce the time and resources needed to develop an effective model for a specific task, leveraging the extensive learning done during the pre-training phase.

### Transformers and PyTorch Frameworks

In this course you will take advantage of `transformers`, a framework developed by 🤗Hugging Face, to have easy access to state-of-the-art models.

Instruction

**Review the Transformers Documentation**: Take a moment to browse the [Transformers Documentation](https://huggingface.co/docs/transformers/index) and bookmark the site as this is a page you will revisit often throughout this course.

Note

**PyTorch Framework**: In addition to Transformers API, you will also be using PyTorch as the preferred ML framework.

### Transformers and Pytorch Set-Up

Begin by installing Transformers and PyTorch in your environment:

```python
conda install transformers torch
```

See how easy it is to get started using a pre-trained BERT model using transformers:

```python
# import the specific tokenizer and model
from transformers import BertTokenizer, BertModel

# instantiate tokenizer object using the correct configurations
tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')

# instantiate the model using the pretrained weights
model = BertModel.from_pretrained('bert-base-uncased')

text = 'This is a simple text string to pass to the model.'

# tokenize the text using Pytorch (note: if TensorFlow, return_tensors='tf')
encoded_input = tokenizer(text, return_tensors='pt')

# produces the model output
output = model(**encoded_input)
```

With just a few lines of code, you are on your way to using pre-trained models.

Warning

**Correct Version of Python for PyTorch**: PyTorch on Windows currently only supports Python 3.8 - 3.11. In case you have the latest version of Python (3.12), you need to install a version between 3.8 and 3.11 so that PyTorch will install properly. If not, you may run into errors that do not explicitly say that the Python version is the problem.

### Conclusion

In this reading, you learned the basics of pre-trained models and got an overview of how the pre-training is done. Also, you set up your environment with Transformers and PyTorch frameworks to get ready to work with the pre-trained models.

As you proceed in the course, you will learn more about these models and get an in-depth understanding of a BERT’s variation called DistilBERT.