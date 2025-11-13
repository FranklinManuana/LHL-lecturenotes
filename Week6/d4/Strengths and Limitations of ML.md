## Strengths and Limitations of Machine Learning

As you have seen, ML is being employed in the industry in a multitude of ways. Organizations who fail to adopt machine learning and data-driven approaches risk getting left behind. But, like all technologies, machine learning is no magic bullet. It comes with its own strong and weak spots. A good data scientist needs to be aware of and to understand the strengths and limitations inherent in the technology.

### Strengths

#### 1. Automation

A key benefit offered by machine learning is that it drives efficiency by automating several routine tasks that previously needed human intervention.

Self-driving cars are a popular example of machine learning and AI automation, as well as ChatGPT.

Fraud detection, loan application decisions etc. are some more examples of machine learning algorithms that have replaced or augmented human decision-makers.

#### 2. Continuous Improvement

A big advantage offered by machine learning is the ability of algorithms to improve over time.

As more data is collected, stored and fed into these models, the algorithm becomes more ‘experienced’ and therefore gets more accurate.

A perfect example of such continuous improvement offered by machine learning is in recommendation systems such as those in Netflix. As it learns more about your past movie choices and what you liked and did not like, the algorithm gets better at suggesting the right kind of movies that you would like to watch.

#### 3. Data-Driven Policies

Traditional algorithms typically reflect rule-based heuristics which are decided ‘a priori’, i.e., before the fact.

Whereas machine learning literally requires learning from the data, that is an ‘a posteriori’, i.e., a data-driven approach to solving problems.

A good example of this is in spam detection. A rule-based spam detection algorithm will fail against new kinds of spam emails whereas machine learning algorithms which can continually learn will eventually learn to detect them.

### Limitations

#### 1. Biases

Machine learning algorithms are as susceptible to humans as unintentionally letting biases and prejudices creep into the decision-making process.

A machine learning algorithm that was used to help Amazon make hiring decisions is a noteworthy example. The recruitment algorithm was found to be biased against women. It penalized candidate resumes that included the word “women’s” such as in “all women’s college” or “captain of women’s team”. There are several similar instances of bias in algorithms used to determine credit worthiness, crime patrolling etc.

While humans are equally if not more susceptible to such biases, bias in ML can be harder to root out since the bias may be stemming from complex models.

Typically there are three key reasons why biases may impact a machine learning model:

1. There are biases in the input training data
2. There is improper or incomplete model development without explicitly paying attention to bias avoidance
3. There is a lack of awareness about the social context the machine learning algorithm operates in.

#### 2. Bad Data or Limited Data

Garbage in, garbage out (GIGO) is an old concept but in the age of machine learning, this saying is more relevant than ever before.

Most machine learning models need sufficient data to provide useful predictions.

If the data provided is incorrect, the model will learn incorrect relationships.

Also, bias in the input data that reflect past decisions made by biased human decision makers such as in hiring or credit loan approvals will lead to the machine learning model also learning these biases.

#### 3. Models are Stochastic

Deterministic models are those where the output of the model is fully determined by the inputs to the model, and the model parameters.

Stochastic models on the other hand carry some inherent randomness. Therefore, for the same input values, the model may generate different outputs.

Most machine learning algorithms are stochastic in nature. This is because reality does contain inherent randomness and incorporating this into models is necessary to build robust and realistic models.

However, on the flip side, it can be hard to justify different outcomes for similar or identical inputs. For example, a [CBC Marketplace investigative report](https://www.cbc.ca/news/science/dna-ancestry-kits-twins-marketplace-1.4980976) discovered that ancestry DNA testing companies yielded widely different ancestry results for two people even though they were twins. This also might make the models less reliable and harder to interpret in some cases.