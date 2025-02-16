# Machine Learning Engineering by Andriy Burkov

Source: [mlebook.com](http://mlebook.com/).

## Table of contents

1. Introduction
    - Data and Machine Learning Terminology
    - When to Use Machine Learning
    - What is Machine Learning Engineering
    - Machine Learning Project Life Cycle
2. Before the Project Starts
    - Prioritization
    - Estimating Complexity
    - Defining the Goal
    - Structuring a Machine Learning Team
    - Why Machine Learning Projects Fail

## 1. Introduction

### Data and Machine Learning Terminology

- Data can be used __directly__ or __indirectly__. Directly used data is a biasis for forming a dataset of examples, such as product sales. Indirectly-used data is used to enrich those examples, such as promotional data.
- __Raw__ data is a collection of entities in their natural form, which cannot always be used for machine learning directly. A __tidy__ dataset can be seen as a spreadsheat where each row is an example, and each column is one of the properties of an example. In addition to being tidy, most machine learning algorithms require numerical data, as opposed to categorical. __Feature engineering__ is the process of transforming data into a form that machine learning algorithms can use.
- Data should be split up into three sets: a __training__ set, a __validation__ set and a __test__ set. The learning algorithm uses the training set to produce the model. The validation set is used to compare different models and choose the best model. The test set is used to assess the the final model performance. Since the validation and test set are not used for training the model, they are called __holdout sets__.
- A __baseline__ is a very simple algorithm that is used to make sure that a new mdel works better than a simple heuristic.
- A machine learning __pipeline__ is a sequence of operations on the dataset that goes from its initial state to the model. This pipeline contains chained stages of data transformation, from data partitioning to missing-data imputation, to class imbalance and dimensionality reduction, to model trainng. The hyperparameters of the entire pipeline are usually optimized, the entire pipeline can be deploted and used for predictions.
- A __model-based__ learning algorithm uses the training data to create a model with __parameters__ learned from the training data, such as __support vector machines__ (SVM). An __instance-based__ learning algorithm uses the whole dataset as the model, such as __k-Nearest Neighbours__ (kNN).
- __Shallow learning__ algorithms learn the parameters of the model directly from the features of the training examples. A __deep learning__ algorithm trains a layered model, in which each layer generates outputs by taking the outputs of the preceding layer as inputs.
- __Model training__ is the process of applying a machine learning algorithm to a dataset in order to obtain a model. __Model scoring__ is the process of applying a trained model to an input sample in order to obtain a prediction.

### When to Use Machine Learning

You should consider using machine learning to solve a business problesm when the problem is __too complex for coding__, the problem is __constantly changing__, it is a __perceptive problem__, it is an __unstudied phenomenon__, the problem has a __simple objective__, and it is __cost-effective__.

Machine learning should,probably, not be used when __explainability is needed__, when __errors are intolerable__, when __traditional software engineering__ is less expensive, when __all inputs and outputs can be enumerated__ and saved in a database, and when __data is hard to get__ or __too expensive__.

### What is Machine Learning Engineering

Machine learning engineering (MLE) is the use of scientific principles, tools and techniques of machine learning and traditional software engineering to design and build complex computing systems. MLE encompasses all stages from data collection, to model training, to making the model available for use by the product or the customers.

A machine learning engineer typically works closely together with a data analyst, who is concerned with understanding the business problem, building the model to solve it, and evaluating the model in a restructed development environment. The machine learning engineer, in turn, is concerned with sourcing the data from various systems and locations and preprocessing it, programming features, training and effective model that will run in the production environment, coexist well with other production precesses, be stable, maintainable, and easily accessible by different types of users with different use cases.

### Machine Learning Project Life Cycle

![Machine Learning Project Lifecycle](machine-learning-project-lifecycle.png)

Some considerations:

- A business analyst works with the client and data analyst to transform a business problem into an __engineering project__. This project may or may not contain a machine learning part.
- In the scope of a broader engineering project, machine learning must first have a well-defined __goal__. This should be a specification of what a statistical model receives as input, what is generates as output, and the criteria of acceptable (or unnacceptable) behavior of the model. This goal is not necessarily the same as the __business objective__. The business objective is what the organization wants to achieve.

## 2. Before the Project Starts

### Prioritization

The key considerations in the prioritization of a machine learning project, are __impact__ and __cost__.

The impact of using machine learning is high when:

1. machine learning can replace a complex part in your engineering project, or
2. there's a great benefit in getting inexpensive (but probably imperfect) predictions.

The cost of a machine learning project is highly influenced by three factors:

1. the __difficulty of the problem__
    - whether an implementation capable of solving the problem is already available
    - whether significant computation power is needed to build the model or run it in the production environment
2. the __cost of data__ 
    - whether you can get the right data and the right amount
    - whether data can be generated automatically
    - what the cost of manual annotation is
    - how many examples are needed
3. the needed model __performance quality__ 
    - whether a complex architecure is required for the desired performance
    - how costly each wrong prediction is
    - what the lowest accuracy level below which the model becomes impractical is

### Estimating Complexity
  
In a machine learning project, there are several __major unknowns__ that are almost impossible to guess:

- Whether the required level of model performance is attainable in practice,
- How much data you will need to reach that level of performance
- What features and how many features are needed
- How large the model should be
- How long it will take to run one experiment
- How many experiments will be needed to reach the desired level of performance

One way to make a more educated guess is to __simplify the problem__ and solve a simpler one. For example, make a subselection of classes to preduct, or split the problem into several simple ones by using the natural slices in the available data.

The progress of machine learning projects is __nonlinear__. The error usually decreases fast in the beginning, but then the progress slows down. Making sure that the client understands the constraints and the risks is important. It can help to log every activity and track the time it took, this is also useful for estimating complexity for similar projects in the future

### Why Machine Learning Projects Fail

A machine learning project can fail for many reasons, and mosy actually do. Typical reasons for failure are:

- Lack of __experienced talent__
  - Having experience with the entire machine learning project life cycle.
- Lack of __support by the leadership__
  - Often, the problem lies in the inability of scientists to communicate the results and challenges to upper management. Because they don’t share the vocabulary and have very different levels of technical expertise, even a success presented badly can be seen as a failure.
- Missing data __infrastructure__
- __Data labeling__ challenge
- __Siloed organizations__ and lack of __collaboration__
  - Typical reasons for mistrust between teams is the lack of understanding by the engineers of the tools and approaches used by the scientists and the lack of knowledge (or plain ignorance) by the scientists of software engineering good practices and design patterns.
- Technically __infeasible__ projects
  - It is best, at least in the beginning, to focus on achievable projects, involving simple collaboration between teams, easy to scope, and targeting a simple business objective.
- Lack of __alignment__ between technical and business teams
  - Without continuous feedback from the business team on the achievement of a business objective, the scientists often reach an initial level of model performance, and then they are not sure if they are making any useful progress and whether an additional effort is worth it.

## 3. Data collection and Preparation

### Questions about the data

Before you start collecting the data, there are five questions to answer: 

- Is the data __accessible__?
  - Physically, contractually, ethically, or from a cost perspective
  - Sensitive data: anonymize to remove personally identifiable information (PII)
- Is the data __sizeable__?
  - How frequently is new data generated?
  - Way to check if you have collected sufficient data is to plot __learning curves__: plot the training and validation scores of your learning algorithm for varying numbers of training examples, see figure below. Upon reaching a vertain number of training examples, you will begin to experience diminishing returns from additional examples.
  - Some practitioners use rules of thumb to estimate the number of training examples needed. However, this is largely dependend on problem domains. Some frequently cited numbers:
    - 10 times the amount of features (often exaggerates the size of the training set, can be used as upper bound)
    - 100 or 1000 times the number of classes (often underestimates the size)
    - 10 times the number of trainable parameters (usually applied to neural networks)

![Learning curves](learning-curves.png)

- Is the data __useable__?
  - 
- Is the data understandable?
- Is the data reliable?

### Common problems with data

- High cost
- Bad quality
- Noise
- Bias
  - Types of
  - Ways to avoid
- Low predictive power
- Outdated examples
- Outliers
- Data leakage

### What is good data

Good data:

- contains enough information that can be used for modeling,
- has good coverage of what you want to do with the model,
- reflects real inputs that the model will see in production,
- is as unbiased as possible,
- is not a result of the model itself,
- has consistent labels, and
- is big enough to allow [[generalization]].

### Dealing with interaction data

...

### Causes of data leakage

- Target is a function of a feature
- Feature hides the target
- Feature from the future

### Data partitioning

Conditions for data splitting:

1. Split was applied to raw data
2. Data was randomized before the split
3. Validation and test sets follow the same distribution
4. Leakage during the split was avoided

- Leakage during partitioning

### Dealing with missing attributes

- Data imputation techniques
- Leakage during imputation

### Data augmentation

- Data augmentation for images
- Data augmentation for text

### Dealing with imbalanced data

- Oversampling
- Undersampling
- Hybrid strategies

### Data sampling strategies

- Simple random sampling
- Systematic sampling
- Stratified sampling

### Storing data

- Data formats
- Data storage levels
- Data versioning
- Documentation and metadata
- Data lifecycle

### Data manipulation best practices

- Reproducibility
- Data first, algorithm second
