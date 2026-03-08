### 3.1 Random variables | 随机变量

- **Definition**: A random variable (r.v.) is a function from the sample space $S$ to the real numbers $\mathbb{R}$.
- **Mechanism**: The randomness of an r.v. originates from the experiment itself; before the experiment is performed, the outcome $s \in S$ is unknown, and the r.v. $X$ has a range of possible values. After the experiment, the outcome $s$ is realized, and the r.v. crystallizes into a numerical value $X(s)$.
- **Notation**: Random variables are typically denoted by capital letters like $X, Y, Z$.
- **Indicator Random Variable | 指示随机变量**: A specific type of r.v. that indicates whether an event occurs, assigning 1 to "yes" and 0 to "no".

### 3.2 Distributions and probability mass functions | 分布与概率质量函数

- **Discrete Random Variable | 离散随机变量**: An r.v. that has a finite or countably infinite list of possible values $a_1, a_2, \dots$ such that $P(X = a_j \text{ for some } j) = 1$.
- **Support | 支撑集**: The set of values $x$ for which $P(X = x) > 0$.
- **Probability Mass Function (PMF) | 概率质量函数**: For a discrete r.v. $X$, the PMF is the function $p_X(x) = P(X = x)$.
- **Validity Criteria**: A function is a valid PMF if it is nonnegative ($\geq 0$) and sums to 1 over its support.
- **Renormalization**: If a joint PMF is conditioned on an event, the remaining probabilities are divided by the total probability of that event to ensure the new conditional PMF sums to 1.

### 3.3 Bernoulli and Binomial | 伯努利分布与二项分布

- **Bernoulli Distribution ($Bern(p)$)**: An r.v. representing a single Bernoulli trial with success probability $p$ and failure probability $q = 1-p$.
    - $P(X=1) = p$.
    - $P(X=0) = 1-p$.
- **Binomial Distribution ($Bin(n, p)$)**: The distribution of the number of successes in $n$ independent Bernoulli trials, each with success probability $p$.
    - **PMF**: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$ for $k \in {0, 1, \dots, n}$.
    - **Symmetry**: If $X \sim Bin(n, p)$, then $n-X \sim Bin(n, 1-p)$.

<aside> 💡

伯努利分布是只有1和0作为结果的实验，二项分布是重复做n次独立的伯努利实验，每次成功的概率是p，X是成功的次数

</aside>

### 3.4 Hypergeometric | 超几何分布

- **Story**: Consider an urn with $w$ white balls and $b$ black balls. If $n$ balls are drawn _without replacement_, the number of white balls $X$ follows a Hypergeometric distribution.
- **PMF**: $P(X = k) = \frac{\binom{w}{k}\binom{b}{n-k}}{\binom{w+b}{n}}$ for valid integers $k$.
- **Isomorphism**: The distribution arises in any scenario involving two sets of "tags" where at least one set is assigned randomly (e.g., elk capture-recapture, aces in a poker hand).
- **Symmetry**: $HGeom(w, b, n)$ and $HGeom(n, w+b-n, w)$ are identical distributions.

### 3.5 Discrete Uniform | 离散均匀分布

- **Story**: Choosing one number uniformly at random from a finite, nonempty set of numbers $C$.
- **PMF**: $P(X = x) = 1/|C|$ for all $x \in C$.
- **Sampling**: In a group of $n$ items, the probability that a specific item is included in a sample of size $k$ is $k/n$, regardless of whether sampling is with or without replacement (though the joint distributions differ).

### 3.6 Cumulative distribution functions (CDF) | 累积分布函数

- **Definition**: $F_X(x) = P(X \leq x)$.
- **Relation to PMF**: For discrete r.v.s, the height of a jump in the CDF at $x$ is equal to $P(X = x)$.
- **Properties of a valid CDF**:
    1. **Increasing**: If $x_1 \leq x_2$, then $F(x_1) \leq F(x_2)$.
    2. **Right-continuous**: $\lim_{x \to a^+} F(x) = F(a)$.
    3. **Limits**: $\lim_{x \to -\infty} F(x) = 0$ and $\lim_{x \to \infty} F(x) = 1$.

<aside> 💡

**PMF和CDF的区别和联系**

**PMF（probability mass function）**

- 只用于**离散型**随机变量。
    
- 直接给每个点的概率：
    
    $p_X(x)=P(X=x)$
    
- 像“表格/直方图”：每个取值占多少概率。
    

**CDF（cumulative distribution function）**

- **离散、连续都能用**（更通用）。
    
- 给累计概率：
    
    $F_X(x)=P(X\le x)$
    
- 像“累计曲线”：到 x 为止一共累积了多少概率。 </aside>
    

### 3.7 Functions of random variables | 随机变量的函数

- **Concept**: If $X$ is an r.v., then $g(X)$ is also an r.v. that maps outcomes $s$ to $g(X(s))$.
- **PMF of $g(X)$**: $P(g(X) = y) = \sum_{x: g(x)=y} P(X = x)$.
- **One-to-One Transformation**: If $g$ is one-to-one, then $P(g(X) = g(x)) = P(X = x)$.
- **Category Error | 范畴错误**: A common mistake involving the confusion of distributions, random variables, events, and numbers.
- **Equality vs. Distribution**: Two r.v.s having the same distribution ($X \sim Y$) does not mean they are always equal as functions ($X = Y$).

<aside> 💡

相当于是一种映射，将随机变量的分布映射到包含随机变量的函数的分布

</aside>

### 3.8 Independence of r.v.s | 随机变量的独立性

- **Definition**: R.v.s $X$ and $Y$ are independent if $P(X \leq x, Y \leq y) = P(X \leq x)P(Y \leq y)$ for all $x, y \in \mathbb{R}$.
- **Discrete Case**: Equivalent to $P(X = x, Y = y) = P(X = x)P(Y = y)$ for all $x, y$.
- **I.I.D.**: Independent and identically distributed random variables.
- **Representation**: $X \sim Bin(n, p)$ can be represented as $X = X_1 + \dots + X_n$ where $X_j$ are i.i.d. $Bern(p)$.
- **Sum of Binomials**: If $X \sim Bin(n, p)$ and $Y \sim Bin(m, p)$ are independent, then $X+Y \sim Bin(n+m, p)$.

### 3.9 Connections between Binomial and Hypergeometric | 二项分布与超几何分布的联系

- **Binomial to Hypergeometric (Conditioning)**: If $X \sim Bin(n, p)$ and $Y \sim Bin(m, p)$ are independent, the conditional distribution of $X$ given $X+Y=r$ is $HGeom(n, m, r)$.
- **Hypergeometric to Binomial (Limit)**: As the population size $N = w+b \to \infty$ with $p = w/(w+b)$ fixed, the $HGeom(w, b, n)$ distribution converges to $Bin(n, p)$.

### 3.10 Recap | 总结

- Distributions can be specified via a PMF, a CDF, or a story.
- The four fundamental objects of probability—distributions, r.v.s, events, and numbers—are all interconnected.