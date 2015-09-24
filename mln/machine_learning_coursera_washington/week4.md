# ml - coursera (washington) - week 4

## k-nearest neighbors

- : introduction

    - : key idea
        - just store all training examples $\langle x_i, f(x_i) \rangle$

    - nearest-neighbor
        - given query instance $x_q$
        - first locate nearest training example $x_n$
        - then estimate $\hat{f}(x_q) \leftarrow f(x_n)$

    - k-nearest neighbor
        - given $x_q$
        - take vote among its k nearest neighbors (if discrete)
        - take mean of $f$ values of k nearest neighbors (if continuous)

    - : advantages
        - training is very fast
        - learn complex functions easily
        - don't lose information

    - : disavantages
        - slow at query time
        - lots of storage
        - easily fooled by irrelevant atttributes

- : representation

    - : distance measures
        
        - : numeric features
            - euclidean, manhatan, l-norm
            - $L^n(x_1, x_2) = \sqrt[n]{\sum^{dim}_{i=1} | x_{1,i} - x_{2,i} | ^n}$
            - normalized by range, std. deviation

        - : symbolic features
            - hamming/overlap
            - value difference measure (vdm)
            - $\delta(val_i, val_j) = \sum^{|classes|}_{h=1}|P(c_h|val_i) - P(c_h|val_j)|^n$

        - : in general
            - arbitrary, encode knowledge

    - : voronoi diagram
        
        - S: training set
        - voronoi cell of $x \in S$:
        - all points closer to $x$ than to any other instance in S
        - region of class C:
        - union of voronoi cells of instances of C in S

    - : behavior in the limit

        - $\epsilon^*(x)$: error of optimal prediction
        - $\epsilon_{NN}(x)$: error of nearest neighbor
        - theorem: $lim_{n \rightarrow \infty} \le 2 \epsilon^*$
        - proof sketch (2-class case):
        - $\epsilon_{NN} = p_+ p_{NN \epsilon -} + p_- p_{NN \epsilon +}$
        - $\epsilon_{NN} = p_+ (1 - p_{NN \epsilon +} + (1 - p_+) p_{NN \epsilon +}$
        - $lim_{n \rightarrow \infty} p_{NN \epsilon +} = p_+$
        - $lim_{n \rightarrow \infty} p_{NN \epsilon -} = p_-$
        - $lim_{n \rightarrow \infty} \epsilon_{NN} = p_+ (1 - p_+) + (1 - p_+) p_+$
        - $lim_{n \rightarrow \infty} \epsilon_{NN} = 2 \epsilon^\* (1 - \epsilon^\*) \le 2 \epsilon^\* $
        - $lim_{n \rightarrow \infty} (Nearest neighbor) = Gibbs Classifier$
        - theorem: $lim_{n \rightarrow \infty, k \rightarrow \infty, k/n \rightarrow 0} \epsilon_{knn} = \epsilon$

    - distance weighted k-nn

        - weight nearer neighbors more heavily
        - $\hat{f}(x_q) = \frac{\sum^{k}_{i=1} w_i f(x_i)}{\sum^{k}_{i=1} w_i}$
        - $w_i \equiv  \frac{1}{d(x_1, x_i)^2}$
        - makes sense to use all training examples, instead of k
        - in practice, limit to k due performance issues

- curse of dimensionality

    - nearest-neighbor is easily misled when hi-dim X
    - easy problems in low-dim are hard in hi-dim
    - low-dim intuitions don't apply in hi-dim
    - : examples
        - normal distribution
        - uniform distribution on hypercube
        - points on hypergrid
        - approximation of sphere by cube
        - volume of hypersphere

- : overfitting avoidance

    - set k by-cross validation
    - form prototypes
    - : remove noisy features
        - remove x if all x's k nearest neighbors are of another class

- : feature selection
    
    - : filter approach
        - pre-select features individually
        - example: by info gain

    - : wrapper approach
        
        - run learner with different combinations of features
        
        - : forward selection

                Forward_Selection(FS)
                    FS: Set of features used to describe examples
                Let SS = {}
                Let BestEval = 0
                Repeat
                    Let BestF = None
                    For each feature F in FS and not in SS
                        Let SS' = SS U {F}
                        If Eval(SS') > BestEval
                        Then let BestF = F
                             let BestEval = Eval(SS')
                    If BestF <> None
                    Then let SS = SS U {BestF}
                Until BestF = None or SS = FS
                Return SS

        - : backward elimination

                Backward_Elimination(FS)
                    FS: Set of features used to describe examples
                Let SS = FS
                Let BestEval = Eval(SS)
                Repeat
                    Let WorstF = None
                    For each feature F in SS
                        Let SS' = SS - {F}
                        If Eval(SS') >= BestEval
                        Then let WorstF = F
                             let BestEval = Eval(SS')
                    If WorstF <> None
                    Then let SS = SS - {WorstF}
                Until WorstF = None or SS = {}
                Return SS

- : feature weighting

    - stretch jth axis by weight $z_j$
    - where $z_1, ..., z_n$ chosen to minimize prediction error
    - use gradient descent to find weights $z_1, ..., z_n$
    - setting $z_j$ to zero eliminates this dimension altogether

- : computational cost

    - efficient retrieval
        - k-d trees (only work inlow dimensions)

    - efficient similarity comparison
        - use cheap approximations to weed out most instances
        - use expensive measure on remainder

    - form prototypes

    - edited k-nn
        
        - remove instances that don't affect frontier
        
        - : backward

                Edited_k-NN(S)
                    S: set of instances
                For each instance x in S
                    If x is correctly classified by S - {X}
                        Remove x from S
                Return S

        - : forward

                Edited_k-NN(S)
                    S: set of instances
                T = {}                    
                For each instance x in S
                    If x is not correctly classified by T
                        Add x to T
                Return T

## other forms of instance-based learning

- locally weighted regression

    - k-nn forms local approximation to f for each query point
    - fit linear function to k nearest neighbors
    - fit quadratic
    - produces piecewise approximation to f
    - : choices of error to minimize
        - squared error over k-nn nearest neighbors
        
        - $ E_1(x_q) = \sum_{x \in kNN(x_q)} (f(x) - \hat{f}(x))^2$
        - distance-weighted squared error over all neighbors
        - $E_2(x_q) \equiv \sum_{x \in D} (f(x) - \hat{f}(x))^2 K(d(x_q, x))$

- radial basis functions networks

    - : representation
        - global approximation
        - in terms of linear combinations of local approximations
        - different kind of neural network
        - closely related to distance-weighted regression
        - but eager instead of lazy
        - target function
        - $f(x) = w_0 + \sum^{k}_{u=1} w_u K_u (d(x_u, x))$
        - kernel function 
        - $K_u(d(x_u, x)) = e^{- \frac{1}{2 \sigma^2_u} d^2(x_u, x)}$

    - : training

        - : what $x_u$ to use for each kernel function

            - scatter uniformly through instance space
            - use training instances (reflects distribution)
            - cluster instances and use centroids

        - : how to train weights (assume gaussian $K_u$)

            - first choose variance (perhaps mean) for each $K_u$
            - then hold $K_u$ fixed, and train linear output function
            - efficient methods to fit linear function
            - or use backpropagation

- case-based reasoning

    - can apply instace-based even when $X \ne \mathbb{R}^n$
    - need different "distance" measure
    - applied to instances with symbolic logic description

    - cadet
        - instances represented by rich structural descriptions
        - multiple cases retrieved (and combined) to form solutions to new problems
        - tight coupling between case retrieval and problem solving

## lazy vs. eager learning

- : lazy
    - wait for query before generalizing
    - can create many local approximations
    - can represent more complex functions (if same H)
    - k-nn, case-based reasoning

- : eager
    - generalize before seeing query
    - must create global approximations
    - id3, foil, naive bayes, ann,   etc

## collaborative filtering

- : problem
    - predict wheter someone will like something
    - look at what similar users liked
    - similar users = similar likes and dislikes

- : representation
    - each user by vector of ratings
    - implicit and explicit

- : predict rating
    - $\hat{R}_{ik} = \bar{R}_i + \alpha \sum_{X_j \in N_i} W_{ij}(R_{jk} - \bar{R}_j)$
    - $\alpha = (\sum |W_{ij}|)^{-1}$
    - $\hat{R_{ik}} = \alpha \sum_{X_j \in N_i} W_{ij} R_{jk}$ (primitive version)
    - $N_i$ can be whole database or k nearest neighbors
    - $R_{jk}$ = rating of user j on item k
    - $\bar{R_j}$ = average of all user j's ratings
    - in principle, any prediction method can be used

- : similarity
    - pearson coefficient
    - $W_{ij} = \frac{\sum_k (R_{ik} - R_i) (R_{jk} - R_j)}{\sqrt{\sum_k (R_{ik} - R_i)^2 (R_{jk} - R_j)^2 }}$
    - summation in pearson is over all items rated by both users



