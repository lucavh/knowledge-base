Tree-based learning is a prominent machine learning technique widely used in data science for both classification and regression tasks. It involves constructing decision trees, hierarchical structures that recursively split data into subsets based on the values of input features. These trees facilitate the prediction of target variables by traversing from the root node to leaf nodes, where predictions are made.

### Construction of Decision Trees

1. **Feature Selection**: The algorithm selects the most informative feature as the root node based on criteria like Gini impurity, entropy, or mean squared error.
2. **Splitting Nodes**: Nodes are divided into child nodes by selecting feature thresholds that optimize a certain criterion (e.g., maximizing information gain or minimizing impurity).
3. **Recursion**: The process is repeated recursively, creating a tree with internal nodes and leaf nodes representing predictions.
    
### Types of Tree-Based Models

1. **Decision Trees**: Simple tree structures used for classification and regression tasks. They are prone to overfitting on complex datasets.
2. **Random Forest**: An ensemble method that combines multiple decision trees to improve predictive accuracy and mitigate overfitting.
3. **Gradient Boosting**: A boosting technique that builds trees sequentially, each correcting the errors of the previous one, leading to enhanced model performance. Examples of these models are [[xgboost]] and [[lightgbm]].    

### Advantages

- **Interpretability**: Decision trees provide a transparent representation of decision-making processes, making them valuable for understanding model predictions.
- **Handling Non-Linearity**: Tree-based models are well-suited for capturing complex nonlinear relationships in data.
- **Variable Importance**: These models can quantify the importance of features, aiding in feature selection and identifying key predictors.
- **[[ensemble-learning]]**: Random forests and gradient boosting improve predictive power by aggregating multiple trees, often outperforming individual decision trees.
- **Handling Mixed Data**: Tree-based models can handle mixed data types (categorical and numerical) without extensive preprocessing.

### Tree-based [[ensemble-learning]]

| Bagging | Boosting |
| ------- | -------- |
| e.g. **boostrap** and **random forest** | e.g. **AdaBoost** and **(hist-)gradient boosting** |
| fits trees **independently** | fits trees **sequentially** |
| each **deep** tree **overfits** | each **shallow** tree **underfits** |
| averaging the tree predictions reduces **overfitting** | sequentially adding trees reduces **underfitting** |

Gradient boosting tends to perform slightly better than bagging and random forest. Furthermore, shallow trees predict faster.

Tree-based learning has found extensive use in various domains of data science, including finance, healthcare, marketing, and more. By harnessing the power of decision trees and their ensembles, data scientists can develop accurate and interpretable models that excel in predictive tasks involving complex data structures.

[[classification]] [[regression]] [[learning-algorithms]]