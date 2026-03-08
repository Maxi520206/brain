#Probability 
[[KB3.3.1-Set Theory Basic]]
[[KB3.2.1-Basic Concept]]

#### 1.1 Set Theory | 集合论

- **Sample Space | 样本空间**: The set $S$ of all possible outcomes of a particular experiment.
- **Event | 事件**: Any collection of possible outcomes (a subset of $S$).
- **Elementary Set Operations | 基本集合运算**:
    - **Union | 并集**: $A \cup B = {x : x \in A \text{ or } x \in B}$.
    - **Intersection | 交集**: $A \cap B = {x : x \in A \text{ and } x \in B}$.
    - **Complement | 补集**: $A^c = {x : x \notin A}$.
- **Key Properties | 关键性质**:
    - **Commutativity | 交换律**, **Associativity | 结合律**, **Distributive Laws | 分配律**.
    - **DeMorgan’s Laws | 德·摩根定律**: $(A \cup B)^c = A^c \cap B^c$ and $(A \cap B)^c = A^c \cup B^c$.
- **Disjoint Sets | 互斥集**: Two events are disjoint if $A \cap B = \emptyset$.
- **Partition | 划分**: A collection of pairwise disjoint sets $A_1, A_2, \dots$ such that $\cup_{i=1}^{\infty} A_i = S$.

#### 1.2 Probability Theory | 概率论

##### 1.2.1 Axiomatic Foundations | 公理化基础

- **Sigma Algebra | $\sigma$ 代数**: A collection of subsets $\mathcal{B}$ closed under complementation and countable unions, containing $\emptyset$.
- **Probability Function | 概率函数**: A function $P$ with domain $\mathcal{B}$ satisfying **Kolmogorov Axioms**:
    1. $P(A) \ge 0$ for all $A \in \mathcal{B}$.
    2. $P(S) = 1$.
    3. **Countable Additivity | 可列可加性**: For pairwise disjoint $A_1, A_2, \dots$, $P(\cup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} P(A_i)$.

##### 1.2.2 The Calculus of Probabilities | 概率演算

- **Basic Properties**:
    - $P(\emptyset) = 0$, $P(A) \le 1$, $P(A^c) = 1 - P(A)$.
    - $P(B \cap A^c) = P(B) - P(A \cap B)$.
    - $P(A \cup B) = P(A) + P(B) - P(A \cap B)$.
- **Inequalities | 不等式**:
    - **Bonferroni’s Inequality | Bonferroni 不等式**: $P(A \cap B) \ge P(A) + P(B) - 1$.
    - **Boole’s Inequality | Boole 不等式**: $P(\cup_{i=1}^{\infty} A_i) \le \sum_{i=1}^{\infty} P(A_i)$.

##### 1.2.3 Counting | 计数

- **Fundamental Theorem of Counting | 计数基本定理**: If a job consists of $k$ tasks with $n_i$ ways each, the total ways are $n_1 \times n_2 \times \dots \times n_k$.
- **Counting Methods (Selecting $r$ from $n$) | 计数方法总结**:
    1. **Ordered, without replacement**: $n! / (n-r)!$.
    2. **Ordered, with replacement**: $n^r$.
    3. **Unordered, without replacement**: $\binom{n}{r} = \frac{n!}{r!(n-r)!}$ (**Binomial Coefficient | 二项式系数**).
    4. **Unordered, with replacement**: $\binom{n+r-1}{r}$.

##### 1.2.4 Enumerating Outcomes | 结果枚举

- **Equally Likely Outcomes**: If all outcomes in finite $S$ are equally probable, $P(A) = \frac{\text{number of elements in } A}{\text{number of elements in } S}$.

#### 1.3 Conditional Probability and Independence | 条件概率与独立性

- **Conditional Probability | 条件概率**: $P(A|B) = \frac{P(A \cap B)}{P(B)}$ if $P(B) > 0$.
- **Bayes’ Rule | 贝叶斯法则**: For a partition $A_1, A_2, \dots$, $P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{j=1}^{\infty} P(B|A_j)P(A_j)}$.
- **Statistical Independence | 统计独立性**: $A$ and $B$ are independent if $P(A \cap B) = P(A)P(B)$.
- **Mutual Independence | 相互独立**: For a collection of events, the product rule must hold for every subcollection.

#### 1.4 Random Variables | 随机变量

- **Definition**: A random variable (r.v.) is a function from the sample space $S$ into the real numbers $\mathbb{R}$.
- **Induced Probability | 诱导概率**: $P_X(X \in A) = P({s \in S : X(s) \in A})$.

#### 1.5 Distribution Functions | 分布函数

- **Cumulative Distribution Function (cdf) | 累积分布函数**: $F_X(x) = P_X(X \le x)$ for all $x$.
- **Properties of cdf**:
    1. $\lim_{x \to -\infty} F(x) = 0$ and $\lim_{x \to \infty} F(x) = 1$.
    2. $F(x)$ is nondecreasing.
    3. $F(x)$ is right-continuous | 右连续: $\lim_{x \downarrow x_0} F(x) = F(x_0)$.
- **Classification**:
    - **Continuous r.v.**: $F_X(x)$ is a continuous function.
    - **Discrete r.v.**: $F_X(x)$ is a step function.
- **Identically Distributed | 同分布**: $X$ and $Y$ are identically distributed if $F_X(x) = F_Y(x)$ for all $x$.

#### 1.6 Density and Mass Functions | 密度与质量函数

- **Probability Mass Function (pmf) | 概率质量函数**: For discrete r.v. $X$, $f_X(x) = P(X = x)$.
- **Probability Density Function (pdf) | 概率密度函数**: For continuous r.v. $X$, $f_X(x)$ satisfies $F_X(x) = \int_{-\infty}^x f_X(t) dt$.
- **Validity Conditions**:
    - Discrete: $f_X(x) \ge 0$ and $\sum_x f_X(x) = 1$.
    - Continuous: $f_X(x) \ge 0$ and $\int_{-\infty}^{\infty} f_X(x) dx = 1$.