DBSCAN is a density-based [[clustering-algorithms]] that looks for areas of high density and assigns clusters to them, whereas points in less dense regions are not even included in the clusters and labeled as anomalies. It has two key settings:

- _eps_: maximum distance between two points to consider them as neighbours. If this distance is too large we might end up with all the points in one huge cluster, however, if it is too small we might not even form a single cluster.
- _min_points_: minimum number of points to form a cluster. If we set a low value for this parameters we might end up with a lot of really small clusters, however, a large value can stop the algorithm from creating any clusters at all.

![Example of DBSCAN](DBSCAN_search.gif)