K-Means is a popular unsupervised clustering algorithm used to partition a dataset into 'k' distinct clusters. It works by iteratively assigning data points to the nearest cluster center (centroid) and then updating the centroids based on the mean of the points within each cluster. The algorithm converges when the centroids no longer change significantly.

The downside of k-means is that
- it requires the number of clusters to be predefined.
- clusters must be circular shaped, k-means has no way of accounting for differently shaped clusters, such as oblong or elliptical.

### Example

Suppose we have a dataset of 2D points representing customers based on their spending habits (annual income vs. spending score) in a mall. We want to group these customers into three clusters to target them with specific marketing strategies.

1. **Initialization**: Randomly select three points as initial cluster centroids.
2. **Assignment**: Assign each customer to the nearest centroid based on Euclidean distance. Customers in the same cluster share similar spending habits.
3. **Update Centroids**: Calculate the mean of the points within each cluster and update the centroid position.
4. **Re-Assignment and Update**: Repeat steps 2 and 3 until the centroids stabilize (convergence).
5. **Result**: The algorithm converges, and we obtain three clusters of customers based on their spending habits.

![Example of K-means](kmeans.gif)

K-Means is an iterative process and may depend on the initial centroids, so it's common to run the algorithm multiple times and choose the best result. The final clustering enables businesses to tailor marketing strategies to different customer segments, maximizing sales and customer satisfaction.

[[clustering-algorithms]]


