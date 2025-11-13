## Hierarchical Clustering

A _connectivity-based clustering_, also known as _hierarchical clustering_, is based on the core idea of objects being more related to the nearby objects than to the objects farther away. These algorithms connect "objects" to form "clusters" based on their distance. A cluster can then be described largely by the maximum distance needed to connect the parts of the cluster.

At different distances, different clusters will form, which can be represented using _a dendrogram_, which explains where the common name _"hierarchical clustering"_ comes from. These algorithms do not provide a single partitioning of a dataset, but instead provide an extensive hierarchy of clusters that merge at certain distances.

In _a dendrogram_, the y-axis marks the distance at which the clusters merge, while the objects are placed along the x-axis so that the clusters don't mix.

The following image is an example of a hierarchical cluster analysis diagram, sourced from [https://uc-r.github.io/hc_clustering](https://uc-r.github.io/hc_clustering)

![Hierarchical cluster analysis diagram](https://learningimages.lighthouselabs.ca/Data%20BC/Machine%20Learning/Unsupervised%20Learning/Hierarchical-Clustering-1.png)

Instruction

Watch the video below to better understand how `hierarchical clustering` works: