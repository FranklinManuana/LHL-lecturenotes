**LLM Project Activity**: This is your LLM project activity. Following this activity, you will work on creating the project submission, the _LLM Model Report_ (as explained towards the end of this activity).

## Introduction

Evaluating and optimizing the project model is your last project task. To optimize the performance of your model, you will implement some of your findings from the optimization task (_Optimizing LLM Performance_). This will involve retraining your model using the changes to the hyperparameters of your choosing. As an added bonus, feel free to also fine-tune multiple models for a point of comparison.

## Instructions

Follow the instructions given here to evaluate and optimize your project model:

- Create a free account on Hugging Face if you have not already done so. Create an access token with write access that will allow you to push your models to the model hub.
    
    Note
    
    This process will automatically save all model assets and even create a model card for you. If set to public, your model can be used by others, helping to further the NLP community.
    
- To begin, use the following code snippet to authenticate your notebook to send your model to the hub.
    
    ```python
    from huggingface_hub import notebook_login
    notebook_login()
    ```
    
    Warning
    
    You will be met with a prompt to enter your access code which you can find in your Hugging Face account.
    
- Additionally, you will need `git-lfs` due to the size of the model and its assets:
    
    ```python
     !apt-get install git-lfs
    ```
    
    Note
    
    **Installing Git Large File Storage (LFS)**: Instructions to install LFS for different operating systems are given [here](https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage?platform=mac).
    
- At this time, repeat all the steps to train your model. Make the changes to your TrainingArguments object which you will pass to your Trainer object. At minimum, be sure to include the following arguments:
    
    ```python
    repo_name = "your-repo-name"
    training_args = TrainingArguments(
       output_dir=repo_name,
       push_to_hub=True,
    )
    ```
    
- Once training is complete, take a look at the performance of your model:
    
    ```python
    trainer.evaluate()
    ```
    
- Once you are happy with the results, push your model to the hub for later use and share with the NLP community:
    
    ```python
    trainer.push_to_hub()
    ```
    
- Now that you have saved your model, go to the url and see what is produced when you push your model to the hub:
    
    `https://huggingface.co/user-name/repo-name`
    
- Browse through each of the tabs and get familiar with what you find in each one.Take some time on the `Files and versions` tab to appreciate how much of the complexity of training has been taken away using the Hugging Face API.
    
- Finally, you can use this model to predict on new text unseen with ease by the model using the pipelines module:
    
    ```python
    from transformers import pipeline
    data = [list of text data you want to predict] 
    my_model = pipeline(model="user-name/repo-name")
    my_model(data)
    ```
    

Question

Now that you have these predictions, can you evaluate the performance of the model on this unseen data?

Warning

**Optimization Time**: The time to optimize a model will vary from project to project, as explained below.

The time it takes to optimize a model depends on the following factors:

- Size of dataset
- Complexity of dataset
- NLP task chosen for the project
- Pre-trained model chosen for the project

Therefore, different individuals in the cohort may take different time (anywhere from 30 minutes to a couple of hours) to optimize their project model. However, evaluating the project model won’t take that long.

Note

**Next Steps for Bootcamp Learners**: Now that you have successfully fine-tuned a pre-trained model specific to your task, optimized its performance, and pushed it to the hub for future use, it’s time to jump to the [LLM project page](https://web.compass.lighthouselabs.ca/p/ds-flex-2/projects/ds-llm) and create the _LLM Model Report_. Note, this report is your project submission and will be evaluated.

Note

**Next Steps for Alumni**: Now that you have successfully fine-tuned a pre-trained model specific to your task, optimized its performance, and pushed it to the hub for future use, it’s time to create a report on your LLM model in the next activity _LLM Model Report_.