Unsupervised learning deals with the task of learning similarities and associations in unlabeled data.

Unlike supervised learning which makes use of labeled data, that is, data with target labels, unsupervised learning searches for patterns and infers underlying associations in datasets without labels.

For instance in the following image, an image recognition algorithm is being trained on pictures of fruits. In order to train such an algorithm, it is simply fed images of several fruits and the algorithm attempts to cluster images. Contrast this with supervised learning where the dataset would include labels along with the images of different fruits.

![An image recognition algorithm](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/image+recognition+algorithm.png)

Note

The lack of target labels in the dataset makes unsupervised learning often more difficult in practice than supervised learning. Since, there are no target labels, it is also difficult to know what the unsupervised algorithm should optimize for.

The performance of a supervised learning algorithm can be measured by studying how well it performs at predicting the value of interest among the observations held out in a test set.

However, with unsupervised learning, since we do not know the “right answer” or “true label” for any observation, it is not possible to easily check the performance of an unsupervised learning algorithm.

Regardless of these limitations, unsupervised learning methods are still an important tool in the data scientist’s toolkit. They have found several applications and in some cases, have led to the emergence of entirely new industries.

### Successful Use Cases

**a. Customer Segmentation** Online retailers routinely try to identify groups or clusters of shoppers with similar purchasing patterns. This lets them tailor and target marketing campaigns, as well as display items that are more likely to be purchased by shoppers of a particular group.

![Customer Segmentation](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/Customer+Segmentation.png)

Image: A simple illustrative example of a customer segmentation performed on the basis of age and income.

**b. Targeted advertising** Likewise, a search engine might selectively display targeted ads or highlighted search results to individuals based on the browsing patterns of similar individuals.

**c. Anomaly Detection** The market for internet of things (IoT) based services surpassed $100 billion in revenue in 2017 and forecasts predict it will be a trillion dollar industry by 2025. However, with the growth in IoT, as more and more devices are interconnected, security threats also multiply. Specific unsupervised learning algorithms known as anomaly detection methods come in handy in identifying malicious actors.

Anomaly detection, also sometimes known as outlier detection, is useful in identifying anomalous data or observation that differs substantially from other routine non-malicious observations. This is useful in identifying and flagging unusual usage patterns by hackers.

**d. Cybersecurity** In combination with supervised learning methods discussed previously, banks also resort to such unsupervised anomaly detection algorithms to flag fraudulent transactions. Likewise, many websites such as LinkedIn use unsupervised learning algorithms to identify the click patterns of web crawlers to stop them from harvesting confidential or proprietary data.

**e. Medical research** In medical research, scientists employ unsupervised learning algorithms to search for patterns among the genetic sequences of patients in order to identify sub-types of a particular disease to obtain a better understanding.

### A Deeper Dive into Unsupervised Learning

Let us take a holistic look at the pipeline for an unsupervised learning project.

![Pipeline for an unsupervised learning project](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/Pipeline+for+an+unsupervised+learning+project.png)

**Step 1.** Since unsupervised learning can be thought of as “machine learning without labels”, we first need some historical unlabeled data to train the algorithm and search for patterns, groups, clusters, or associations between observations.

**Step 2.** In unsupervised learning, as with all kinds of machine learning applications, we need to know the purpose of our exercise at the outset. Are we looking to segment customers to better target ads? Are we searching for anomalous users who may be hackers? Are we searching for web crawlers and scrapers?

Answering this question will allow us to focus on the right set of features that are relevant to our problem. If we are looking to segment customers for targeted ads, the demographic information of customers will be a useful feature. If we are searching for hackers, then, features related to clicks will be useful.

**Step 3.** The data is then used to train an appropriately chosen unsupervised learning algorithm that is suited to the task at hand. In the rest of this unit, we will discuss some foundational clustering and association algorithms, each with their strengths and weaknesses.

**Steps 4 and 5.** Once the model is trained, and after we extract the clusters or associations identified by the model in the data, we check for internal and external validity of our model.

**Internal validation** consists of evaluating the goodness of model outputs in terms of whether observations identified as belonging to the same cluster are closer to one another than to observations in other clusters. That is, it verifies that there is within-cluster similarity and across-cluster dissimilarity.

**External validation** involves a manual analysis of the unsupervised learning outputs and identification of whether the uncovered clusters or associations are meaningful.

![External validation](https://learningimages.lighthouselabs.ca/Data+BC/Machine+Learning/Intro+to+ML/External+validation.png)

For example, in the above clustering example, the unsupervised learning algorithm will only identify the presence of three clusters in the data. It then requires the data scientist or other domain experts to put meaningful labels on these clusters. In this example, the unsupervised learning algorithm appears to have uncovered three truly meaningful clusters in the dataset which can now be used for purposes such as targeted marketing.

Note

Often, an unsupervised learning algorithm will be internally valid but the clusters uncovered by the algorithm may not correspond to meaningful groups and therefore it is said to fail external validity. If this turns out to be the case, then the model results will be of limited practical utility.