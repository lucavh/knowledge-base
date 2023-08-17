You can determine the optimal number of clusters for a data set with the following two measures:

- __Elbow method__: determine the elbow point of the graph, in the example it's clearly k=4. Unfortunately, the elbow is not always as sharp, i.e. the data is not as clearly clustered.
- __Silhouette method__: in more ambiguous cases, this metric measures how similar a point is to its own cluster compared to other clusters. The range of the Silhouette value is between -1 and +1 and the higher it is, the better.

![Elbow method](elbow-method.png)
![Silhouette method](silhouette-method.png)

[[clustering-algorithms]]
[[model-evaluation]]