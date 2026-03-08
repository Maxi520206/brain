### 1.1 Why study probability?

- **Goal**: Probability provides a logical framework for quantifying uncertainty and randomness in a principled way.
- **Intuition**: It aims to strengthen intuition in fields like science and everyday life where initial guesses are often deeply counterintuitive.

### 1.2 Sample spaces and Pebble World

- **Sample Space | 样本空间 $S$**: The set of all possible outcomes of an experiment.
- **Outcome | 结果 $s$**: A single possible result of an experiment, visualized as a "pebble".
- **Event | 事件 $A$** : A subset of the sample space $A \subseteq S$. An event occurred if the actual outcome is an element of that subset.
- **Set Theory Operations**:
    - **Union | 并集 $A \cup B$** : $A$ or $B$ (inclusive).
    - **Intersection | 交集 $A \cap B$** : $A$ and $B$ .
    - **Complement | 补集 $A^c$** : Not $A$ .
    - **Mutually Exclusive | 互斥**: $A$ and $B$ are mutually exclusive if $A \cap B = \emptyset$ .
    - **Partition | 划分**: A collection of events $A_1, \dots, A_n$ such that they are disjoint and their union is $S$
- **Pebble World Representation**:
    - If the sample space is finite, outcomes can be visualized as pebbles.
    - The "mass" of a pebble represents its probability.
    - If all pebbles have the same mass, outcomes are equally likely (the basis for the naive definition).

### 1.3 Naive definition of probability

- **Definition | 定义**: Let $A$ be an event for an experiment with a finite sample space $S$ . The naive probability of $A$ is: $P_{naive}(A) = \frac{|A|}{|S|} = \frac{\text{number of outcomes favorable to } A}{\text{total number of outcomes in } S}$ .
- **Restrictive Assumptions**: This definition only applies if outcomes are equally likely.
- **Complements**: $P_{naive}(A^c) = 1 - P_{naive}(A)$ . This is often a useful strategy when the complement is easier to count.

### 1.4 How to count

- **Multiplication Rule | 乘法原理**: If a compound experiment consists of two sub-experiments where Experiment A has $a$ outcomes and Experiment B has $b$ outcomes for each outcome of A, then there are $ab$ total outcomes.
    - Chronological order is not required; the rule applies regardless of which sub-experiment is performed first.

**1.4.1 Sampling with replacement**: Choosing $k$ objects from $n$ with replacement where order matters results in $n^k$ outcomes.

**1.4.2 Sampling without replacement**: Choosing $k$ objects from $n$ without replacement where order matters results in: $n(n-1)\dots(n-k+1) = \frac{n!}{(n-k)!}$ .

- **Permutations**: If $k = n$, the number of ways to arrange all $n$ objects is $n!$ .

**1.4.3 Binomial coefficient | 二项式系数**:

- **Definition**: Denoted as $\binom{n}{k}$ , read as "n choose k". It is the number of subsets of size $k$ for a set of size $n$ .
- **Formula**: $\binom{n}{k} = \frac{n(n-1)\dots(n-k+1)}{k!} = \frac{n!}{k!(n-k)!}$ .
- **Adjustment for Overcounting**: $\binom{n}{k}$ is found by taking the number of ordered samples and dividing by $k!$ (the number of ways to reorder those $k$ elements), since order does not matter in a subset.
- **Binomial Theorem | 二项式定理**: $(x+y)^n = \sum_{k=0}^n \binom{n}{k} x^k y^{n-k}$ .

**1.4.4 Bose-Einstein**: Choosing $k$ times from a set of $n$ objects with replacement, if order **does not** matter (counting how many times each object was chosen): $\text{Number of possibilities} = \binom{n+k-1}{k}$ .

- This is isomorphic to putting ( k ) indistinguishable particles into $n$ distinguishable boxes.
- **Warning**: While this counts unordered samples, these samples are typically **not equally likely** in real-world scenarios (like the birthday problem), so the naive definition of probability often does not apply.

### 1.5 Story proofs

- **Definition**: A proof by interpretation. It involves counting the same set of objects in two different ways to prove a mathematical identity.
- **Key Examples**:
    - **Choosing the complement**: $\binom{n}{k} = \binom{n}{n-k}$ (Choosing who is on a committee is the same as choosing who is left off).
    - **The Team Captain**: $n \binom{n-1}{k-1} = k \binom{n}{k}$ (Choosing a team and then a captain vs. picking a captain first and then the rest of the team).
    - **Vandermonde’s Identity**: $\binom{m+n}{k} = \sum_{j=0}^k \binom{m}{j} \binom{n}{k-j}$ (Choosing a committee of size $k$ from a group of $m$ juniors and $n$ seniors by summing the possible number of juniors selected).

### 1.6 Non-naive definition of probability

- **General Definition**: A probability space consists of a sample space ( $S$ ) and a probability function ( $P$ ) that maps events to numbers in ( ).
- **Axioms of Probability | 概率公理**:
    1. $P(\emptyset) = 0 , P(S) = 1$ .
    2. **Countable Additivity**: If $A_1, A_2, \dots$ are disjoint events, then $P(\cup_{j=1}^\infty A_j) = \sum_{j=1}^\infty P(A_j)$ .
- **Derived Properties**:
    - $P(A^c) = 1 - P(A)$ .
    - **Inclusion-Exclusion**: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ .
    - General Inclusion-Exclusion for $n$ events involves alternating sums of probabilities of all possible intersections.

### 1.8 R

- **Basic Commands**:
    - `factorial(n)`: Computes ( n! ).
    - `choose(n, k)`: Computes ( \binom{n}{k} ).
    - `sample(n, k, replace=TRUE/FALSE)`: Generates random samples with or without replacement.
- **Simulation**: `replicate(10^4, experiment)` allows running a probabilistic experiment many times to estimate probabilities empirically.