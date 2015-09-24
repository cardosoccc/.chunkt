# ml - coursera (washington) - week 3

## introduction

- learning sets of rules
    - variable size
    - deterministic
    - discrete and continuous (mixed)
    - constructive search
    - eager
    - batch

## representation

- relationship to decision trees
    
    - any decision tree can be converted into a set of rules

    - replication problem
        - a small set of rules can correspond to a big decision tree

- rule set hypothesis space
    - each rule is a conjunction of tests
    - each test has the form $x_j = v$, $x_j \le v$, or $x_j \ge v$
    - a rule set is a disjunction of rules

## learning algorithms

- : propositional
    
    - learning a single rule
        - start with an empty rule
        - add tests one at a time
        - until the rule covers only positive examples
        - : algorithm

                GrowRule(S)
                R = {}
                repeat
                    choose best test x_j theta_v to add to R, where theta in {=, <>, <=, >=}
                    S := S - all examples that do not satisfy R U {x_j theta_v}
                until S contains only positive examples

    - choosing the best test

        - current rule $R$ covers $m_0$ negative examples and $m_1$ positive examples
        - let $p = \frac{m_1}{m_0+m_1}$
        - proposed $R \cup {x_j\theta_v}$ covers $m'_0$ and $m'_1$ examples
        - let $p' = \frac{m'_1}{m'_0+m'_1}$
        - $Gain = m'_1[(-p log_2 p) - (-p' log_2 p')]$
        - we want reduce surprise
        - but also want want the rule to cover many examples

    - learning a set of rules (separate-and-conquer)

            GrowRuleSet(S)
            A = {}
            repeat
                R := GrowRule(S)
                Add R to A
                S := S - all positive examples that satisfy R
            until S is empty
            return A

    - more thorough search rules

        - : round-robin replacement
            - after growing complete rule set
            - delete the first rule
            - compute the set S of training examples not covered by any rule
            - add one or more rules to cover S
            - can be repeated with each original rule

        - : backfitting
            - after each new rule add
            - perform few iterations of round-robin replacement
            - repeat until all positive examples are covered

        - : beam search
            - instead of growing one new rule, grow B new rules
            - consider adding each possible test to each rule
            - keep the best B resulting rules
            - when no more tests are added
            - choose the best of B rules and add to rule set

    - probability estimates from small numbers
        
        - laplace estimate
            - add 0.5 no numerator
            - add 1 to denominator
            - $p = \frac{m_1 + 0.5}{m_0 + m_1 + 1}$

        - general prior estimate
            - add any $k$ to numerator
            - add any $xk$ to denominator
            - $\frac{k}{xk}$ represents the prior belief
            - the larger $k$ the stronger the prior belief becomes

    - learning rules for multiple classes
        - order rules
        - decision list
        - weighted vote
        - weight = accuracy x coverage

- : foil

    - first-order inductive learner
        - same as propositional separate-and-conquer, except:
        - different candidate specializations (literals)
        - different evaluation function

    - learning first-order rules
        - can learn set of rules such as
        - $ancestor(x, y) \leftarrow parent(x, y)$ 
        - $ancestor(x, y) \leftarrow parent(x, z) \wedge ancestor(z, y)$
        - predicate logic, not only propositional
        - prolog programs are sets of such rules

    - specializing rules in foil
        
        - : learning rule
            - $P(x_1, x_2, ..., x_k) \leftarrow L_1 ... L_n$
        
        - : literals
            - $Q(v_1, ..., v_r)$ - where at least one $v_i$ must exist as a variable in the rule
            - $Equal(x_j, x_k)$ - where $x_j$ and $x_k$ are variables present in the rule
            - the negation of either of the above

    - information gain in foil

        - $FoilGain(L, R) \equiv t( log_2 \frac{p_1}{p_1 + n_1} - log_2 \frac{p_0}{p_0 + n_0} )$
        - $L$ is the candidate literal to add to rule $R$
        - $p_0$ - number of positive bindings of $R$
        - $n_0$ - number of negative bindings of $R$
        - $p_1$ - number of positive bindings of $R + L$
        - $n_1$ - number of negative bindings of $R + L$
        - $t$ - number of positive bindings of $R$ also covered by $R + L$

- : inverse resolution

    - : induction as inverted deduction

        - induction is finding an $h$ such that
        - $( \forall \langle x_i, f(x_i) \rangle \in D) B \wedge h \wedge x_i \vdash f(x_i)$
        - $x_i$ - the $ith$ training example
        - $f(x_i)$ - target function value for $x_i$
        - $B$ - background knowledge

    - : advantages

        - subsumes earlier idea of finding $h$ that "fits" data
        - domain theory $B$ helps define meaning of "fit" the data
        - suggests algorithms that search $H$ guided by $B$

    - : disadvantages

        - does not allow noisy data
        - huge hypothesis space
        - overfitting
        - intractability of calculating all acceptable $h$'s

    - deduction - resolution rule

        - given initial clauses $C_1$ and $C_2$
        - find literal $L$ from clause $C_1$ such that $\neg L$ occurs in clause $C_2$
        - form resolvent $C$ including all literals from $C_1$ and $C_2$
        - except for $L$ and $\neg L$
        - $C = (C_1 - \\{L\\}) \cup (C_2 - \\{\neg L\\})$

    - inverting propositional resolution

        - given initial clauses $C_1$ and $C$
        - find literal $L$ that occurs in clause $C_1$
        - but not in clause $C$
        - form the second clause $C_2$ by including the following literals:
        - $C_2 = (C - (C_1 - \\{L\\})) \cup \\{\neg L\\}$

    - first-order resolution

        - find a literal $L_1$ from clause $C_1$
        - find a literal $L_2$ from clause $C_2$ 
        - and substitution $\theta$ such that $L_1 \theta = \neg L_2 \theta$
        - form resolvent $C$ by including all literals from $C_1 \theta$ and $C_2 \theta$
        - except for $L_1 \theta$ and $\neg L_2 \theta$
        - $C = (C_1 - \\{L_1\\}) \theta \cup (C_2 - \\{L_2\\}) \theta$

    - inverting first-order resolution

        - $C_2 = (C - (C_1 - \\{L_1\\}) \theta_1) \theta_2^{-1} \cup \\{ \neg L_1 \theta_1 \theta_2^{-1} \\}$

    - : algorithms
        
        - cigol
            - basic algorithm
        
        - progol

            - reduce combinatorial explosion

            - generating most specific acceptable $h$

            - user specifies $H$ stating allowed predicates, functions and form of arguments for each

            - : sequential covering algorithm
                - for each $\langle x_i, f(x_i) \rangle$
                - find most specific hypothesis such that $B \wedge h_i \wedge x_i \vdash f(x_i)$
                - considers only k-step entailment

            - conduct general to specific search bounded by specific hypothesis $h_i$
            - choosing hypothesis with minimum description length

## summary

- rule grown by adding one antecedent at a time
- rule set grown by adding one rule at a time
- propositional or first-order
- alternative: inverse resolution

