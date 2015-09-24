# ml - coursera (washington) - week 2

## introduction

- learning decision trees
    - variable size
    - deterministic
    - discrete and continuous (mixed)
    - constructive search
    - eager
    - batch (there are online algorithms)

- decision tree decision boundaries
    - divide the feature space into axis-parallel rectangles
    - label each rectangle with one of the k classes

- inductive bias
    - occam's razor
    - prefer the simplest hypothesis that fits the data

## representation

- decision tree representation
    - any boolean function
    - in worst case require exponentially many nodes
    - disjunction of conjunctions

- decision tree hypothesis space

    - internal nodes
        - test the value of particular features
        - branch according to the results of the test

    - leaf nodes
        - specify the class h(x)

    - growing a decision tree
        - as the number of nodes (or depth) increases
        - hypothesis space grows

## learning algorithms

- id3

    - iterative dichotomiser 3
    - ross quinlan - 1986
    - : algorithm

            id3(examples, targetattribute, attributes):
                - create a root node for the tree
                - if all examples are positive, return the single-node tree root, with label = +
                - if all examples are negative, return the single-node tree root, with label = -
                - if attributes is empty
                    - return the single-node tree root, with label = most common value of targetattribute in examples
                - otherwise begin:
                    - choose the best attribute "a"
                    - for each possible value, "v_i", of "a":
                        - add a new tree branch corresponding to a = v_i
                        - let examples_{v_i} be the set of examples that have value a = v_i
                        - if examples_{v_i} is empty:
                            - add a leaf node below this new branch with label = most common value of target attribute in examples
                        - else 
                            - add the subtree id3( examples_{v_i}, targetattribute_{v_i}, attributes - {a} ) below this new branch
                - end
                - return root

- c4.5
    - numerical features
    - uses rule post-pruning

- cart
    - classification and regression trees
    - very similar to c4.5
    - supports regression
    - does not compute rule sets
    - constructs binary trees
    - using feature and threshold with largest information gain at each node

## attribute selection

- surprise
    - $ S(i) = - log_2 p_i $

- entropy
    - average surprise
    - measures the impurity of a collection of examples 
    - $ Entropy(S) = - \sum_{i = 0}^{c} p_i log_2 p_i $

- information gain
    - how well an attribute separates examples according to their classification
    - $ I(A;B) = H(A) - \sum_{b} P(B=b) H(A|B = b) $
    - $ Gain(S, A) = Entropy(S) - \sum_{v \in Values(A)} \frac{S_v}{S} Entropy(S_v) $
    - $ H(A) $ ( or $Entropy(S)$ ) is the same for all
    - works because it is a convex measure

- gini index
    - another option

## overfitting

- : definition
    - consider error of hypothesis $h$ over: 
    - training data: $error_{train}(h)$
    - entire distribution $D$ of data: $error_D(h)$
    - hypothesis $h \in H$ overfits if there is an alternative $h'$ such that:
    - $error_{train}(h) < error_{train}(h')$
    - and $error_D(h) > error_D(h')$

- pruning
    
    - pre-pruning
        - stop growing when data split not statistically significant
        - can fail sometimes
        - chi-square test
    
    - post-pruning
        - grow full tree, then post-prune
        - test accuracy increase for each pruned node 
        - more reliable
        - lots of data, lots of cycles
        - reduced-error pruning
            
                split into training and validation
                do until is harmful:
                    evaluate impact on validation set of pruning each possible node
                    greedly remove the one that most improve validation set

    - rule post-pruning
        - convert tree to equivalent set of rules
        - each leaf is a rule
        - prune each rule independently of others
        - it is not constrained by the tree structure
        - sort final rules into desired sequence for use
        - sort by accuracy
        - classify by majority vote
        - weight by accuracy and coverage
        - perhaps most frequently used method (C4.5)

## other issues

- non-boolean features

    - multiple discrete values

        - : multiway splits
            - avoid when there are lot of values

        - : one-vs-all
            - one hot encoding

        - : group values
            - disjoint subsets

    - real-valued features
        - treshold splits
        - range splits

- learning parity with noise
    - exclusive-or (2-bit parity)
    - decision trees cannot distinguish random noisy features

- attributes with many values

    - use gain ratio
    - sensitive to how broadly and uniformly the attribute splits the data
    - $ GainRatio(S, A) = \frac{Gain(S,A)}{SplitInformation(S, A)} $
    - $ SplitInformation(S, A) = - \sum_{i=1}^{c}\frac{|S_i|}{|S|} log_2 \frac{|S_i|}{|S|} $
    - $S_i$ - subset of $S$ for which $A$ has values $v_i$
    - SplitInformation is the entropy of S with respect to the values of attribute A

- unknown attribute values

    - imputation
    - assign most common value of the attribute
    - assign most common value of the attribute among examples of the same class
    - assign a probability to each value, assign fraction $p_i$ to each descendant
    - classify examples by the same way

- scaling up
    
    - : id3 and c4.5
        - assume data fit in main memory
        - hundreds of thousands of examples
    
    - : sprint and sliq
        - multiple scans of data
        - millions of examples
    
    - : vfdt
        - at most one sequential scan
        - billions of examples