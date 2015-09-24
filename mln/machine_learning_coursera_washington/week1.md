# ml - coursera (washington) - week 1

## introduction

- definition of machine learning
    - automating automation
    - getting computers to program themselves
    - data + output = program

- components of machine learning
    
    - representation
        - decision trees
        - sets of rules
        - instances
        - graphical models
        - neural networks
        - support vector machines
        - model ensembles
    
    - evaluation
        - accuracy
        - precision and recall
        - squared error
        - likelihood
        - posterior probability
        - cost / utility
        - margin
        - entropy
        - k-l divergence

    - optimization
        - combinatorial (greedy search)
        - convex (gradient descent)
        - constrained (linear programming)

- types of learning
    - supervised learning
    - unsupervised learning
    - semi-supervised learning
    - reinforcement learning

- supervised learning
    - inductive learning
    - given training examples (x, f(x)) of an unknown function f
    - find a good approximation to f
    - discrete: classification
    - continuous: regression
    - probability: probability estimation

- two views of learning
    - learning is the removal of uncertainty
    - learning requires guessing a good, small hypothesis class

- two strategies for machine learning
    - develop languages for expressing prior knowlegde
    - develop flexible hypothesis spaces
    - in either case, develop algorithms for finding an hypothesis that fits the data

## key concepts

- training examples
    - an example of the form (x, f(x))

- target function
    - the true function f

- hypothesis
    - the proposed function h believed to be similar to f

- concept
    - a boolean function
    - positive and negative examples

- classifier
    - a discrete-valued function
    - output also known as class or label

- hypothesis spaces
    - the space of all hypothesis that can be output by the learning algorithm

- version space
    - the space of all hypothesis in hypothesis space that have not yet been ruled out by a training example

## framework for hypothesis spaces

- size
    
    - fixed
        - easier to understand

    - variable
        - more useful
        - introduce the problem of overfitting

- randomness

    - deterministic
        - examples are consistent or inconsistent

    - stochastic
        - examples are more likely or less likely

- parameterization
    
    - discrete
        - must be found with combinatorial search methods

    - continuous
        - must be found by numerical search methods

    - mixed
        - symbolic (discrete) and continuous

- search procedure
    
    - direct computation
        - solve for hypothesis directly
    
    - local search
        - start with an initial hypothesis
        - make small improvements
        - until a local optimum
    
    - construtive search
        - start with an empty hypothesis
        - gradually add structure to it
        - until a local optimum

- timing

    - eager
        - analyze training data and construct an explicit hypothesis

    - lazy
        - store training data until test data point is presented
        - construct ad-hoc hypothesis to classify that data point

- online vs. batch

    - for eager algorithms

    - online
        - analyze each training example as presented

    - batch
        - collect training examples
        - analyze them
        - output hypothesis


## ml in practice

- machine learning pipeline
    - understanding domain, prior knowledge and goals
    - data integration, selection, cleaning, pre-processing
    - learn models
    - interpret results
    - consolidate and deploy
    - loop

- key issues in machine learning
    - what are good hypothesis spaces
    - what algorithms can work with these spaces
    - how optimize accuracy on future data points (overfitting)
    - how can we have confidence in the results (statistical question)
    - are some problems computationally intractable (computational question)
    - how can we formulate problems as ml problems (engineering question)