# [[B70C3-Random variables and their distributions]]
- **Random variables | 随机变量**
	- **Definition**: A random variable (r.v.) is a function from the sample space $S$ to the real numbers $\mathbb{R}$
	- **Mechanism**: The randomness of an r.v. originates from the experiment itself; before the experiment is performed, the outcome $s \in S$ is unknown, and the r.v. $X$ has a range of possible values. After the experiment, the outcome $s$ is realized, and the r.v. crystallizes into a numerical value $X(s)$.
	- **Discrete Random Variable | 离散随机变量**: An r.v. that has a finite or countably infinite list of possible values $a_1, a_2, \dots$ such that $P(X = a_j \text{ for some } j) = 1$.
    - **Support | 支撑集**: The set of values $x$ for which $P(X = x) > 0$.
    - **Probability Mass Function (PMF) | 概率质量函数**: For a discrete r.v. $X$, the PMF is the function $p_X(x) = P(X = x)$.

**Bernoulli and Binomial | 伯努利分布与二项分布**

- **Bernoulli Distribution ($Bern(p)$)**: An r.v. representing a single Bernoulli trial with success probability $p$ and failure probability $q = 1-p$.
    - $P(X=1) = p$.
    - $P(X=0) = 1-p$.
- **Binomial Distribution ($Bin(n, p)$)**: The distribution of the number of successes in $n$ independent Bernoulli trials, each with success probability $p$.
    - **PMF**: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$ for $k \in {0, 1, \dots, n}$.
    - **Symmetry**: If $X \sim Bin(n, p)$, then $n-X \sim Bin(n, 1-p)$.

**Hypergeometric | 超几何分布**

- **Story**: Consider an urn with $w$ white balls and $b$ black balls. If $n$ balls are drawn _without replacement_, the number of white balls $X$ follows a Hypergeometric distribution.
- **PMF**: $P(X = k) = \frac{\binom{w}{k}\binom{b}{n-k}}{\binom{w+b}{n}}$ for valid integers $k$.

**Discrete Uniform | 离散均匀分布**

- **Story**: Choosing one number uniformly at random from a finite, nonempty set of numbers $C$.
- **PMF**: $P(X = x) = 1/|C|$ for all $x \in C$.
- **Sampling**: In a group of $n$ items, the probability that a specific item is included in a sample of size $k$ is $k/n$, regardless of whether sampling is with or without replacement (though the joint distributions differ).

**Cumulative distribution functions (CDF) | 累积分布函数**

- **Definition**: $F_X(x) = P(X \leq x)$.
- **Relation to PMF**: For discrete r.v.s, the height of a jump in the CDF at $x$ is equal to $P(X = x)$.
- **Properties of a valid CDF**:
    1. **Increasing**: If $x_1 \leq x_2$, then $F(x_1) \leq F(x_2)$.
    2. **Right-continuous**: $\lim_{x \to a^+} F(x) = F(a)$.
    3. **Limits**: $\lim_{x \to -\infty} F(x) = 0$ and $\lim_{x \to \infty} F(x) = 1$.

**Functions of random variables | 随机变量的函数**

- **Concept**: If $X$ is an r.v., then $g(X)$ is also an r.v. that maps outcomes $s$ to $g(X(s))$.
- **PMF of $g(X)$**: $P(g(X) = y) = \sum_{x: g(x)=y} P(X = x)$.
- **One-to-One Transformation**: If $g$ is one-to-one, then $P(g(X) = g(x)) = P(X = x)$.

<aside> 💡

[**Law of the unconscious statistician (LOTUS) | 无意识统计学家法则**](https://www.notion.so/Law-of-the-unconscious-statistician-LOTUS-317bcf323f7c805f866ed33e567d1295?pvs=21)

- **Theorem | 定理**: If $X$ is a discrete r.v. and $g$ is a function: $E(g(X)) = \sum_{x} g(x) P(X = x)$. </aside>

**Independence of r.v.s | 随机变量的独立性**

- **Definition**: R.v.s $X$ and $Y$ are independent if $P(X \leq x, Y \leq y) = P(X \leq x)P(Y \leq y)$ for all $x, y \in \mathbb{R}$.
- **Discrete Case**: Equivalent to $P(X = x, Y = y) = P(X = x)P(Y = y)$ for all $x, y$.
- **I.I.D.**: Independent and identically distributed random variables.
- **Representation**: $X \sim Bin(n, p)$ can be represented as $X = X_1 + \dots + X_n$ where $X_j$ are i.i.d. $Bern(p)$.
- **Sum of Binomials**: If $X \sim Bin(n, p)$ and $Y \sim Bin(m, p)$ are independent, then $X+Y \sim Bin(n+m, p)$.

---
# [[B70C4-Expectation]]

**Geometric and Negative Binomial | 几何分布与负二项分布**
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

**Poisson | 泊松分布**

- **PMF**: $P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$ for $k \in {0, 1, 2, \dots}$.
- **Moments | 矩**: $E(X) = \lambda$ and $Var(X) = \lambda$.
- **Poisson Paradigm | 泊松范式**: The number of successes in $n$ trials with small success probabilities $p_i$ is approximately $Pois(\lambda)$ where $\lambda = \sum p_i$.

**Connections between Poisson and Binomial | 泊松分布与二项分布的联系**

- **Sum of Poissons | 泊松分布之和**: If $X \sim Pois(\lambda_1)$ and $Y \sim Pois(\lambda_2)$ are independent, $X+Y \sim Pois(\lambda_1 + \lambda_2)$.
- **Poisson to Binomial (Conditioning) | 调节**: Given $X+Y=n$, the conditional distribution of $X$ is $Bin(n, \frac{\lambda_1}{\lambda_1+\lambda_2})$.
- **Binomial to Poisson (Limit) | 极限**: As $n \to \infty$ and $p \to 0$ such that $np = \lambda$, $Bin(n, p)$ converges to $Pois(\lambda)$.
# [[B71C3-Common Families of Distributions]]
#### 3.3 Continuous Distributions | 连续分布

- **Uniform Distribution | 均匀分布**:
    - **pdf**: $f(x | a, b) = \frac{1}{b-a}$ for $x \in [a, b]$.
- **Gamma Distribution | 伽马分布**:
    - **Gamma Function | $\Gamma$ 函数**: $\Gamma(\alpha) = \int_0^\infty t^{\alpha-1} e^{-t} dt$.
    - **Properties**: $\Gamma(\alpha + 1) = \alpha \Gamma(\alpha)$; for integers, $\Gamma(n) = (n-1)!$.
    - **Expectation**: $E X = \alpha\beta$, **Variance**: $Var X = \alpha\beta^2$.
    - **Exponential Distribution | 指数分布**: Special case of Gamma with $\alpha = 1$.
    - **Chi-squared Distribution | 卡方分布**: Special case of Gamma with $\alpha = p/2$ and $\beta = 2$, where $p$ is the degrees of freedom.
- **Normal Distribution | 正态分布**:
    - **pdf**: $f(x | \mu, \sigma^2) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$.
    - **68-95-99.7% Rule**: Probability content within 1, 2, or 3 standard deviations of the mean.
    - **Continuity Correction | 连续性校正**: When using Normal to approximate Binomial, $P(X \le x)$ is approximated as $P(Y \le x + 1/2)$.
- **Beta Distribution | 贝塔分布**:
    - **Usage**: Often used to model proportions as its support is $(0, 1)$.
    - **Expectation**: $E X = \frac{\alpha}{\alpha + \beta}$.
- **Cauchy Distribution | 柯西分布**:
    - **Characteristic**: A symmetric, bell-shaped distribution where the mean and variance do not exist (the integral diverges).
- **Lognormal Distribution | 对数正态分布**: $X$ is Lognormal if $\log X \sim n(\mu, \sigma^2)$.
- **Double Exponential (Laplace) Distribution | 拉普拉斯分布**: $f(x | \mu, \sigma) = \frac{1}{2\sigma} e^{-|x-\mu|/\sigma}$.
# [[B71C4-Multiple Random Variables]]
#### 4.1 Joint and Marginal Distributions | 联合分布与边缘分布

- **Random Vector | 随机向量**: An $n$-dimensional random vector is a function from a sample space $S$ into $\mathbb{R}^n$.
- **Discrete Random Vectors | 离散随机向量**:
    - **Joint PMF | 联合概率质量函数**: $f(x,y) = P(X=x, Y=y)$.
    - **Calculation of Probabilities**: $P((X,Y) \in A) = \sum_{(x,y) \in A} f(x,y)$.
    - **Expectation**: $E g(X,Y) = \sum_x \sum_y g(x,y)f(x,y)$.
- **Marginal PMF | 边缘概率质量函数**:
    - $f_X(x) = \sum_{y \in \mathbb{R}} f_{X,Y}(x,y)$ and $f_Y(y) = \sum_{x \in \mathbb{R}} f_{X,Y}(x,y)$.
    - **Note**: Marginal distributions do not uniquely determine the joint distribution.
- **Continuous Random Vectors | 连续随机向量**:
    - **Joint PDF | 联合概率密度函数**: A function $f(x,y)$ such that $P((X,Y) \in A) = \iint_A f(x,y) dx dy$.
    - **Marginal PDF | 边缘概率密度函数**: $f_X(x) = \int_{-\infty}^{\infty} f(x,y) dy$.
- **Joint CDF | 联合累积分布函数**: $F(x,y) = P(X \le x, Y \le y)$.
    - **Relation to PDF**: $f(x,y) = \frac{\partial^2 F(x,y)}{\partial x \partial y}$ at continuity points.

#### 4.2 Conditional Distributions and Independence | 条件分布与独立性

- **Conditional PMF/PDF | 条件分布**:
    - $f(y|x) = \frac{f(x,y)}{f_X(x)}$ for $x$ such that $f_X(x) > 0$.
    - **Conditional Expectation**: $E(g(Y)|x) = \int g(y)f(y|x) dy$.
    - **Key Insight**: $E(g(Y)|X)$ is a **random variable** whose value depends on $X$.
- **Independence | 独立性**:
    - $X$ and $Y$ are independent if $f(x,y) = f_X(x)f_Y(y)$ for all $(x,y)$.
    - **Factorization Lemma | 分解引理**: $X$ and $Y$ are independent iff $f(x,y) = g(x)h(y)$ for some functions $g$ and $h$.
    - **Support Condition**: If $X$ and $Y$ are independent, the support of their joint density must be a cross-product set.
- **Properties of Independent r.v.s**:
    - $E(g(X)h(Y)) = (Eg(X))(Eh(Y))$.
    - **MGF of Sum**: $M_{X+Y}(t) = M_X(t)M_Y(t)$.
    - **Sum of Normals**: If $X \sim n(\mu, \sigma^2)$ and $Y \sim n(\gamma, \tau^2)$ are independent, $X+Y \sim n(\mu+\gamma, \sigma^2+\tau^2)$.