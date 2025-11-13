## Introduction

In the previous readings, you learned what pre-trained models are and the process followed to pre-train a model. In this reading, you are going to take a look at BERT a little more closely and understand how BERT and different variations of BERT are used for NLP tasks.

## Reading

As human language can be expressed through a variety of words and the numerous combinations of such words, training a model from scratch on a small dataset would cause overfitting and result in a model that does not generalize well to prediction of new text it is exposed to. This explains the less than ideal performance we saw on the model we built in our last activity.

Transfer learning refers to a paradigm in machine learning where knowledge from a previously trained model can be leveraged to create a new model more specific to the task in the use case. Using pre-trained models for NLP tasks can improve the performance of the model substantially when compared to training your own model from scratch. LLMs have been pre-trained on a large corpus using semi-supervised learning and are ideal for transfer learning applications.

One example of a widely used pre-trained transformer based model is BERT, introduced by Google in 2018. BERT is able to capture context in both directions of a larger text.

Note

Prior to the introduction of transformers, NLP models typically understood text in a sequential fashion from beginning to end. As sentences get longer, less the meaning of the previous text is carried forward to understand subsequent text in entire passages.

The bidirectionality of BERT allows NLP tasks to associate meanings of individual words and their relationships in a larger text in a more comprehensive way.

Note

DistilBERT LLM: BERT (DistilBERT, a variation of BERT, in particular) remains the focus LLM for this course. So, you will learn about BERT (and DistilBERT) in detail in the upcoming sections and activities

### Variations of BERT

BERT comes in many sizes and variations and selection of the appropriate one will be based on your dataset and goals of the NLP task. Generally speaking, given the same model, more parameters and resultant larger model size can lead to a more performant model. A larger model also means a more computationally expensive model during training and higher latency at time of inference. As a reference point, the base BERT model, bert-uncased-base, is trained on ~110M parameters.

Here is a non-exhaustive list of other variations of BERT:

- **BERT**: For question answering (BERT-QA)
- **RoBERTa**: Robustly optimized BERT approach
- **DistilBERT**: Distilled BERT
- **ALBERT**: A Lite BERT
- **ERNIE**: Enhanced Representation through kNowledge Integration
- **BioBERT**: BERT for biomedical QA and text analysis

![Different varitionns of the BERT model](https://learningimages.lighthouselabs.ca/Data+BC/LLM/Unit_4/U4_A01_01.png)

_Fig 1_: Variations of the BERT Model

Some of these aim to improve the original BERT. Some aim to make BERT more applicable by training on domain specific corpora. Some aim to provide a “lighter" version to reduce cost and latency.

Since you are going to use or refer to DistilBERT throughout the course, you will learn about this variation of BERT in detail next.

### DistilBERT – A Lightweight Pre-Trained Model

DistilBERT is a smaller, faster, and more efficient version of the original BERT model, which is a transformer-based ML model for NLP.

BERT has been one of the most influential models in the field of NLP, providing state-of-the-art results on a wide array of NLP tasks. However, its large size and complexity make it computationally expensive, which limits its practical use, especially on devices with limited resources or in applications that require real-time processing.

DistilBERT is created by applying a process called knowledge distillation, which involves training a smaller "student" model to reproduce the behavior of a larger "teacher" model, which is the original BERT in this case. During this process, the student model learns to imitate the teacher model's performance on a specific task. This way, DistilBERT can retain much of the original BERT's language understanding capabilities, but with fewer parameters and increased speed.

Note

Here are some key points about DistilBERT that might further your understanding of the model.

- It has 40% fewer parameters than BERT, which makes it lighter and up to 60% faster.
- It retains over 95% of BERT's performance on many benchmark tasks in NLP.
- Training DistilBERT is generally faster because of its reduced size, meaning that it requires less computational resources.
- DistilBERT is more suitable for environments where resources are constrained, like on mobile devices or in applications with strict latency requirements.

DistilBERT has been widely adopted for tasks where BERT's full capacity may not be required, or where deploying BERT is not feasible due to resource constraints. It provides a good balance between performance and efficiency, making state-of-the-art NLP capabilities more accessible and practical for real-world applications.

## Conclusion

Now that you have learnt the basics of the BERT (and DistilBERT) model, let’s jump to the next reading where you learn about customizing tokenization.