### Anatomy of a learning algorithm

Each learning algorithm consists of three parts:

1. a **loss function**, also called **objective** or **objective function**
2. an **optimization criterion** based on the loss function (e.g. a **cost function** - minimizing the loss function)
3. an **optimization routine** leveraging training data to find a solution to the optimization criterion (such as **gradient descent**)

### Notation & terminology

Typical ML model notation: $f(X,w) = y$, where $X$ is a metrix with all the features and `y` is a vector with the target variable.

As $f_{x}$ is usually unknown, but a sample ($X$) is available, we accept to not find the true values, but the **unbiased estimators**.

### Examples
- [[clustering-algorithms]]

[[inbox/machine-learning]]