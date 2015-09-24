# data analysis and statistical inference - unit 1

## basic concepts

- population
    - all data

- sample
    - subset from population

- data matrix
    - row: observation
    - column: variable

- variables
    
    - numerical (quantitative)
        - continuous
        - discrete
    
    - categorical (qualitative)
        - regular
        - ordinal

- relationships between variables
    
    - : associated
        - dependent
        - positive or negative
    
    - : not associated
        - independent

## studies

- : observational

    - : limitation
        - only establish association
    
    - : retrospective
        - past data
    
    - : prospective
        - data collected throughout the study

- : experiments
    - establish causal connections

- correlation x causation
    - correlation does not imply causation

- counfounding variables
    - variables that affect explanatory and response variable
    - make it seem like there is a relationship between them

- sampling

    - simple random sample
        - each case equally likely to be selected

    - stratified sample
        - divide population into homogeneous strata
        - randomly sample from each stratum

    - cluster sample
        - divide population into clusters
        - randomly sample a few clusters
        - sample all observations within the cluster

    - multistage sample
        - divide population into clusters
        - randomly sample a few clusters
        - randomly sample within these clusters

- bias

    - convenience sample
        - individuals who are easily accessible
        - more likely to be included in the sample

    - non-response
        - if a non-random fraction of the sampled people respond
        - such that the sample is no longer representative

    - voluntary response
        - when the sample consists of people who volunteer
        - because they have strong opinions on the issue

- experimental design
    
    - : principles
        
        - : control
            - compare treatment of interest to a control group

        - : randomize
            - randomly assign subjects to treatments

        - : replicate
            - collect a sufficiently large sample
            - or replicate the entire study

        - : block
            - block for variables that can affect the outcome
            - similar to stratifying
            - blocking during random assignment
            - stratifying during random sampling

    - blocking variables
        - characteristics that we would like to control for

    - explanatory variables
        - factors
        - independent variable
        - conditions imposed on experimental units

    - response variables
        - dependent variable
        - variable under investigation

    - placebo
        - fake treatment used as the control group
        - placebo effect
            - showing change despite being on placebo

    - blinding
        - experimental unit don't know which group they are in
        - double-blind
            - researchers and experimental units don't know group assignment

- random sampling x random assignment

    - random sampling + random assignment
        - ideal experiment
        - causal
        - generalizable

    - random sampling + no random assignment
        - most observational studies
        - not causal
        - generalizable

    - no random sampling + random assignment
        - most experiments
        - causal
        - not generalizable
    
    - no random sampling + no random assignment
        - bad observational studies
        - not causal
        - not generalizable

## measures of center

- mean
    - arithmetic average
    - $\bar{x} = \frac{\sum^{n}_{i=1} x_i}{n}$
    - $\bar{x}$ - sample mean
    - $\mu$ - population mean

- median
    - midpoint of the distribution
    - 50th percentile
    - more robust than the mean

- mode
    - most frequent observation

- : skewness
    
    - : left skewed
        - mean < median

    - : symmetric
        - mean ~ median

    - : right skewed
        - mean > median

## measures of spread

- range
    - max - min

- variance
    - roughly the squared deviation from the mean
    - $s^2 = \frac{\sum^{n}_{i=1} (x_i - \bar{x})^2 }{n-1}$
    - $s^2$ - sample variance
    - $\sigma^2$ - population variance

- standard deviation
    - roughly the average deviation around the mean
    - has the same unit as the data
    - $s = \sqrt{s^2} = \sqrt{\frac{\sum^{n}_{i=1} (x_i - \bar{x})^2 }{n-1}}$
    - $s$ - sample sd
    - $\sigma$ - population sd

- iqr
    - inter-quartile range
    - range of the middle 50% of the data
    - distance between first and third quartile
    - more robust than sd and range
    - $IQR = Q3 - Q1$

## exploring numerical data
    
- scatterplot   
    
    - describe association between variables
    
    - : evaluation

        - : direction
            - positive
            - negative

        - : shape
            - linear
            - curved

        - : strenght
            - weak
            - strong

        - : outliers
            - unusual observations

- histogram
    
    - describe the shape of the distribution
    
    - provide a view of the data density
    
    - : evaluation
        
        - : skewness
            - left skewed
            - symmetric
            - right skewed

        - : modality
            - unimodal
            - bimodal
            - uniform
            - multimodal

        - : bin width
            - can alter the story being told

- dotplot
    - useful when individual values are of interest
    - can get busy as the sample size increases

- boxplot
    - useful for highlighting outliers
    - shows median and iqr

- intensity map
    - useful for highlighting spatial distribution

## exploring categorical data

- frequency table
    - each value of the variable
    - with the count and the frequency

- contingency table
    - shows value counts of two variables
    - last column and last row are the marginal totals

- pie chart
    - avoid
    - differences not clear

- bar plot
    - different from histograms
    - bar plot are for categorical
    - histogram are for numerical

- segmented bar plot
    - useful for visualizing conditional frequency distributions
    - compare relative frequencies to explore relationships

- relative frequency segmented bar plot
    - normalized bar heights

- mosaic plot
    - visualize data from two or more variables
    - independence when boxes across categories have same areas 
    - area of tiles proportional to the number of observations

- side-by-side box plot
    - useful for comparing multiple distributions

## transforming data

- : definition

    - rescale the data using some function
    - useful when data is strongly skewed
    - transform to be easier to model

- : goals
    - see the data structure differently
    - reduce skew
    - straighten a nonlinear relationship

- : transformations

    - log transformation
        - when data cluster near to zero
        - and all observations are positive

    - square root transformation
    - inverse transformation

## introduction to inference

- hypothesis testing framework
    - start with the null hypothesis that represents status quo
    - set an alternative hypothesis that represents the research question
    - conduct a hypothesis test under the assumption that the null is true
    - if data does not provide convincing evidence for alternative
    - stick with the null hypothesis
    - otherwise reject the null hypothesis in favor of the alternative

- null hypothesis
    - $H_0$ - nothing going on

- alternative hypothesis
    - $H_A$ - something going on

- p-value
    - probability of observing an outcome at least as extreme
    - as the one observed in the original data

- simulation
    - set a null and an alternative hypothesis
    - simulate the experiment assuming that the null is true
    - evaluate the p-value
    - if p-value is low, reject the null in favor of the alternative