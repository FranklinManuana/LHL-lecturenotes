**LLM Project Activity**: This is your LLM project activity.

## Introduction

Now that you have selected your project and familiarized yourself with the project workspace, the next step is to access the _ready_ dataset for your project.

## Instructions for Accessing Dataset

Instruction

You first need to import the required module by running the following line of code:

```python
from datasets import load_dataset
```

Based on the project topic you selected in the activity _LLM Project Goals and Objectives_, run the following lines of code to access the dataset corresponding to the selected topic:

- **Sentiment Analysis**:

```python
ds = load_dataset('imdb')
```

```python
ds = load_dataset('yelp_review_full')
```

Warning

Select one of the two datasets given above if your chosen project topic is Sentiment Analysis.

Note

**Additional Info about Datasets**: More information about the two datasets can be found here: [imdb](https://huggingface.co/datasets/imdb) and [yelp**review**full](https://huggingface.co/datasets/yelp_review_full).

- **Document Summarization**:

```python
ds = load_dataset('multi_news')
```

Note

**Additional Info About Dataset**: More information about the dataset can be found here: [multi_news](https://huggingface.co/datasets/multi_news)

- **Topic Modelling**:

```python
ds = load_dataset('SetFit/20_newsgroups')
```

Note

**Additional Info About Dataset**: More information about the dataset can be found here: [SetFit/20_newsgroups](https://huggingface.co/datasets/SetFit/20_newsgroups)

## Using the Datasets

Now that you have saved your dataset in a variable, you can explore a little bit more of what’s contained in it.

Use the `imdb` dataset as an example. The following instructions will hold true regardless of which dataset you choose.

Instruction

To see the available splits for the dataset, run the following code:

```python
ds
>>> DatasetDict({
    train: Dataset({
        features: ['text', 'label'],
        num_rows: 25000
    })
    test: Dataset({
        features: ['text', 'label'],
        num_rows: 25000
    })
    unsupervised: Dataset({
        features: ['text', 'label'],
        num_rows: 50000
    })
})
```

In this case, there are three splits: `train`, `test`, and `unsupervised`. You can see the features of each split and how many rows are contained in each split.

Instruction

To see an example of the first row, use the following line of code:

```python
ds['train'][0]
```

To get a better understanding of the features, you can use the following line of code:

```python
ds['train'].features
```

Note

In case you want to manipulate the data in pandas, you can do so by assigning each split to a DataFrame object. This may come in handy if you want to do some additional data preprocessing to your data such as removing html tags, etc.

```python
import pandas as pd
ds_train = pd.DataFrame(ds['train'])
ds_test = pd.DataFrame(ds['test'])
```

Instruction

Use `df.head()` to explore each of these datasets. After you finish, you want to convert your DataFrames into dataset objects as they have functionality that make it easier to use with the :hugging_face:Hugging Face API.

```python
from datasets import Dataset, DatasetDict
# assign the splits
train = Dataset.from_pandas(ds_train)
test = Dataset.from_pandas(ds_test)
# reconstruct both datasets into a Dataset Dict object
new_ds = DatasetDict(
    {
        'train': train,
        'test': test
    }
)
# view the resulting dataset dict object
new_ds
```

Note

Keep Updating Your Project Journal: As you work towards analysing your dataset, don’t forget to record any observations or findings in the project journal.

## Project Checkpoint

Now that you have laid enough groundwork for your LLM project, it’s time you do a quick check with a mentor and get feedback on your selected project and the corresponding dataset. Once you get a go-ahead from a mentor, you may proceed to the next step in the project the following day.

Instruction

Follow the instructions given here to participate in the project checkpoint.

- Schedule an Assistance Request (AR) with a mentor.
    
- Share a summary of your chosen project with the mentor. Also, share details of the associated dataset.
    

Note

**Refer to Your Project Journal**: As you speak with a mentor and share the summary of your project, you may also refer to your project journal. Remember, you jotted your preliminary ideas related to the chosen project in your journal. So, referring to the journal may support a well-rounded discussion with the mentor.

- Get feedback on the project and the associated dataset. Make sure they share specific feedback on the feasibility of your project and the validity of your dataset.
    
- Implement feedback and make necessary changes to your chosen project (or the dataset) before proceeding with the project the next day.
    

## Conclusion

You will continue working on the project later in the course. Now proceed to learn more about pre-trained models in the next unit.