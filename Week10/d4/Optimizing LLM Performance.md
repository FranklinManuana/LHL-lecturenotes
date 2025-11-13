## Introduction

Previously in the project work, you fine-tuned your model. In this activity, you will consider how you can optimize the model’s performance.

## Instructions

You have already selected the metrics that you will be using to monitor the performance of your model. These are the same metrics you should aim to improve as you optimize the hyperparameters of your model:

- Revisit the `evaluate` module by Hugging Face and make sure the metrics you have chosen are most suitable for your NLP task.
- Follow [this link](https://huggingface.co/docs/evaluate/a_quick_tour) for further reading about metrics and even creating custom metrics.
    
    Note
    
    **Explore Trainer API to Understand Hyperparameters**: Now is the time to dive in a little deeper into the Trainer API to understand the various hyperparameters available to you to help improve the performance of your model.
    
- You were briefly introduced to Trainer API in the previous project task (_Enhance Project Model Using Transfer Learning_) as it was required to train the model. Watch this brief [YouTube video](https://www.youtube.com/watch?v=nvBXf7s7vTI&t=61s) to understand it a little better.
    
    Note
    
    There are LOTS of arguments including hyperparameters that can be tweaked and you can introduce yourself to some of those [here](https://huggingface.co/docs/transformers/v4.35.2/en/main_classes/trainer#transformers.TrainingArguments). At present, the documentation has 101 arguments that can be passed.
    
- Obviously, there is no need to make changes to each and every one of these parameters but here is a list of a few to start with that can make a difference in the output of your model:
    
    - `num_epochs`
    - `per_device_train_batch_size`
    - `per_device_eval_batch_size`
    - `learning_rate`
    - `weight_decay`
    - `warmup_steps`
    
    Warning
    
    These parameters and others will be based on your task and your specific dataset, so take some time to understand the effect of the hyperparameters you choose to change from the default settings.
    

## Conclusion

You have had an opportunity to understand the Trainer API and the TrainingArguments; this will help you work on the final part of your project (_Evaluate & Optimize Project Model_).