### 4.1 Definition of expectation | 期望的定义

- **Concept | 概念**: A single-number summary describing the "average" value of a random variable.
- **Definition (Discrete) | 定义（离散型）**: For a discrete r.v. $X$ with possible values $x_1, x_2, \dots$: $E(X) = \sum_{j=1}^{\infty} x_j P(X = x_j)$.
- **Intuition | 直觉**: It represents the "center of mass" or balancing point of the probability mass function.
- **Center of Mass | 重心**: $E(X)$ depends only on the distribution of $X$, not on the underlying sample space.
- **Pitfall | 误区**: $E(X)$ is a constant, not a random variable. One cannot simply replace $X$ with $E(X)$ in equations without justification.

### 4.2 Linearity of expectation | 期望的线性性质

- **Theorem | 定理**: For any r.v.s $X, Y$ and constant $c$:
    1. $E(X + Y) = E(X) + E(Y)$
    2. $E(cX) = cE(X)$.
- **Dependency | 依赖性**: Linearity holds even if $X$ and $Y$ are dependent.
- **Monotonicity | 单调性**: If $X \geq Y$ with probability 1, then $E(X) \geq E(Y)$.

### 4.3 Geometric and Negative Binomial | 几何分布与负二项分布

- **Geometric Distribution | 几何分布 ($Geom(p)$)**:
    - **Story | 故事**: The number of failures before the first success in independent Bernoulli trials.
    - **PMF**: $P(X = k) = q^k p$ for $k \in {0, 1, 2, \dots}$, where $q = 1 - p$.
    - **Expectation**: $E(X) = \frac{q}{p}$.
- **First Success Distribution | 首中分布 ($FS(p)$)**:
    - **Story | 故事**: Total number of trials until the first success (includes the success).
    - **Relation**: $Y = X + 1$, where $X \sim Geom(p)$.
    - **Expectation**: $E(Y) = \frac{1}{p}$.
- **Negative Binomial Distribution | 负二项分布 ($NBin(r, p)$)**:
    - **Story | 故事**: Number of failures before the $r$-th success.
    - **PMF**: $P(X = n) = \binom{n+r-1}{r-1} p^r q^n$.
    - **Expectation**: $E(X) = r \cdot \frac{q}{p}$ (as it is the sum of $r$ i.i.d. $Geom(p)$ r.v.s).

### 4.4 Indicator r.v.s and the fundamental bridge | 指示随机变量与基本桥梁

- **Indicator R.V. | 指示随机变量**: $I_A = 1$ if event $A$ occurs, and $0$ otherwise.
- **Fundamental Bridge | 基本桥梁**: $P(A) = E(I_A)$. This links probability directly to expectation.
- **Application | 应用**: Used to find expectations of complex r.v.s (like the number of matches in a deck) by decomposing them into a sum of indicators $X = \sum I_i$
- **Expectation via Survival Function | 通过生存函数求期望**: For a non-negative integer-valued r.v. $X$: $E(X) = \sum_{n=0}^{\infty} P(X > n)$.

### 4.5 Law of the unconscious statistician (LOTUS) | 无意识统计学家法则

- **Theorem | 定理**: If $X$ is a discrete r.v. and $g$ is a function: $E(g(X)) = \sum_{x} g(x) P(X = x)$.
- **Significance | 意义**: This allows calculating the expected value of a function of $X$ using only the PMF of $X$, without finding the PMF of $g(X)$ first.

### 4.6 Variance | 方差

- **Definition | 定义**: $Var(X) = E((X - E(X))^2) = E(X^2) - (E(X))^2$.
- **Standard Deviation | 标准差**: $SD(X) = \sqrt{Var(X)}$.
- **Properties | 性质**:
    - $Var(X + c) = Var(X)$.
    - $Var(cX) = c^2 Var(X)$.
    - If $X, Y$ independent: $Var(X + Y) = Var(X) + Var(Y)$.

### 4.7 Poisson | 泊松分布

- **PMF**: $P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$ for $k \in {0, 1, 2, \dots}$.
- **Moments | 矩**: $E(X) = \lambda$ and $Var(X) = \lambda$.
- **Poisson Paradigm | 泊松范式**: The number of successes in $n$ trials with small success probabilities $p_i$ is approximately $Pois(\lambda)$ where $\lambda = \sum p_i$.

### 4.8 Connections between Poisson and Binomial | 泊松分布与二项分布的联系

- **Sum of Poissons | 泊松分布之和**: If $X \sim Pois(\lambda_1)$ and $Y \sim Pois(\lambda_2)$ are independent, $X+Y \sim Pois(\lambda_1 + \lambda_2)$.
- **Poisson to Binomial (Conditioning) | 调节**: Given $X+Y=n$, the conditional distribution of $X$ is $Bin(n, \frac{\lambda_1}{\lambda_1+\lambda_2})$.
- **Binomial to Poisson (Limit) | 极限**: As $n \to \infty$ and $p \to 0$ such that $np = \lambda$, $Bin(n, p)$ converges to $Pois(\lambda)$.

### 4.9 *Using probability and expectation to prove existence | 使用概率与期望证明存在性

- **Probabilistic Method | 概率方法**: A technique to prove the existence of an object with a certain property by showing that a randomly chosen object has that property with non-zero probability.
- **Average Principle | 平均值原理**: There must exist at least one value $\geq E(X)$ and at least one value $\leq E(X)$ in the support.