## Introduction

Previously in the course, you have been able to get a better understanding of how to use the Transformers module. This is a great opportunity to leverage some of these learnings into your project to use a pre-trained model. In this activity, you will utilize a pre-trained model in your project work.

## Instructions

Note

Before you follow the steps given below, it is highly recommended to go through [this resource](https://huggingface.co/docs/transformers/main/en/task_summary) that explains how to use transfer learning on Hugging Face models in a python implementation.

Follow the instructions given here to use a pre-trained model for your project:

- Navigate to [Hugging Face](https://huggingface.co/models) and find a model that has been pre-trained for your specific project task:
    - You can find this by entering the keywords into the models search bar where you see the words “Filter by name.”
- Utilize the pipelines to make inferences using your dataset:

```python
  from transformers import pipelines
```

- Use the pipelines object to choose an NLP task and pre-trained model that you would like to use:
    
    - If you do not pass a model name to the pipelines object, a default model will be selected for you. This is not recommended in production settings.

```python
  # Tasks summary https://huggingface.co/docs/transformers/main/en/task_summary
  pipe = pipeline(task='add the task type here')

  # You can also specify a model to use in the pipeline
  pipe = pipeline(model='add the model name here')
```

Note

**Downloading Pre-Trained Model May Take Time**: The first time the pre-trained model is downloaded, it may take a while since the model assets are usually quite large. Subsequent calls to the pipeline will be significantly faster since they are cached.

- Pass your text data as a list to the pipeline object:

```python
  data = ['list of the text for inference']
  preds = pipe(data)
  preds
```

Instruction

**Inspect the Predictions**: Inspect your predictions from the pre-trained model. If this is a classification task, consider how many labels are available in the dataset.

## Conclusion

**Congratulations**! You have made predictions using a pre-trained LLM. In the upcoming project task (_Enhancing Model Using Transfer Learning_), you will fine-tune your own model. At that time you will be able to compare the differences to the inferences you made here.