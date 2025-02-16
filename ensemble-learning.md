In [[statistics]] and [[machine-learning]], **ensemble methods** use multiple learning algorithms to obtain better than could be obtained from any of the constituent learning algorithms alone.
## Common types of ensembles

### Bayes optimal classifier

The Bayes optimal classifier is a [[classification]] technique. It is an ensemble of all the hypotheses in the hypothesis space. The Naive Bayes classifier is a version of this that assumes that the data is conditionally independent on the class and makes the computation more feasible.
### Bagging (Bootstrap Aggregating)

Bagging creates multiple copies of the same algorithm, each trained on a different subset of the data. These models then vote to make predictions. Random Forest is a popular example of a bagging algorithm, where decision trees work together to make a collective decision.
### Boosting
    
Boosting, on the other hand, focuses on improving the performance of a weak learner (a model that performs slightly better than random chance). It does this by training multiple weak learners sequentially, with each one correcting the mistakes of the previous one. Popular boosting algorithms include AdaBoost and [[gradient-boosting-machines]].
