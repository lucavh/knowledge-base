# Clustering

The three families of clustering algorithms are:

1. __Partional__: k-means and Gaussian Mixture Models (GMM), where k-means is hard assigned version of GMMs and GMMs are able to provide probabilities
2. __Density-based__: DBSCAN and HDBSCAN.
3. __Hierarchical__: either agglomerative or divisive. These may correspond to meaningful taxonomies and a dendrogram can help find the most meaningful number of clusters.

## K-means

The downside of k-means is that

- it requires the number of clusters to be predefined.
- clusters must be circular shaped, k-means has no way of accounting for differently shaped clusters, such as oblong or elliptical.

![Example of K-means](../images/kmeans.gif)

### Hopkins statistic

Determine _clusterability_ using the [_Hopkins statistic_](https://en.wikipedia.org/wiki/Hopkins_statistic). A value of about 0.5 means the dataset does not have a tendency to cluster. If the value of Hopkins statistic is close to zero, the dataset is clusterable.  

### Determine optimal number of clusters

- __Elbow method__: determine the elbow point of the graph, in the example it's clearly k=4. Unfortunately, the elbow is not always as sharp, i.e. the data is not as clearly clustered.
- __Silhouette method__: in more ambiguous cases, this metric measures how similar a point is to its own cluster compared to other clusters. The range of the Silhouette value is between -1 and +1 and the higher it is, the better.

![Elbow method](../images/elbow-method.png)
![Silhouette method](../images/silhouette-method.png)

## Gaussian Mixture Models (GMM)

Instead of a distanced-based model (k-means), GMM uses a distribution-based model. Gaussian Mixture Models are probabilistic models and use a soft clustering approach for distributing the points in different clusters.

![Example of GMM](../images/gmm.gif)

## DBSCAN

DBSCAN looks for areas of high density and assigns clusters to them, whereas points in less dense regions are not even included in the clusters and labeled as anomalies. It has two key settings:

- _eps_: maximum distance between two points to consider them as neighbors. If this distance is too large we might end up with all the points in one huge cluster, however, if it is too small we might not even form a single cluster.
- _min_points_: minimum number of points to form a cluster. If we set a low value for this parameters we might end up with a lot of really small clusters, however, a large value can stop the algorithm from creating any clusters at all.

![Example of DBSCAN](../images/DBSCAN_search.gif)

## Hierarchical Clustering

HDBSCAN is an extension of DBSCAN and and appropriate choice for more randomly distributed data. HDBSCAN is performed over varying epsilon values and the result is integrated, which allows HDBSCAN to find clusters of varying densities - unlike DBSCAN.  

HDBSCAN is a hierarchical, density-based clustering algorithm. There are, however, also pure hierarchical clustering algorithms. These algorithms aim to build a hierarchy of clusters and typically follow one of two approaches:

- __Agglomerative__: a bottom-up approach where each observation starts in its own cluster and pairs of clusters are merged as one moves up the hierarchy
- __Divisive__: a top-down approach where all observations start in one cluster and splits are performed recursively as one moves down the hierarchy.

![Example of agglomerative hierarchical clustering](../images/hierarchical.gif)
