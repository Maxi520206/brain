[[KB3.2.3-Variables Distributions]]
#### 3.1 Introduction | 引言

- **Families of Distributions | 分布族**: Statistical distributions model populations, and a family is indexed by parameters that vary the distribution's characteristics while maintaining a fixed functional form.
- **Parametric Family | 参数族**: A set of distributions described by an unspecified parameter $\theta \in \Theta$.

#### 3.2 Discrete Distributions | 离散分布


- **Hypergeometric Distribution | 超几何分布**:
    - **Story**: Sampling $K$ balls without replacement from an urn with $N$ balls ($M$ red, $N-M$ green).
    - **pmf**: $P(X = x | N, M, K) = \frac{\binom{M}{x} \binom{N-M}{K-x}}{\binom{N}{K}}$ for $x \in {0, 1, \dots, K}$.
    - **Expectation | 期望**: $E X = \frac{KM}{N}$.
    - **Variance | 方差**: $Var X = \frac{KM}{N} \left( \frac{(N-M)(N-K)}{N(N-1)} \right)$.
- **Binomial Distribution | 二项分布**:
    - **Story**: Number of successes in $n$ independent Bernoulli trials with success probability $p$.
    - **Expectation**: $E X = np$.
    - **Variance**: $Var X = np(1-p)$.
- **Poisson Distribution | 泊松分布**:
    - **Asymptotic Property | 渐近性质**: Approximates the Binomial distribution when $n$ is large and $p$ is small such that $np \to \lambda$.
- **Negative Binomial Distribution | 负二项分布**:
    - **Story**: The number of failures $Y$ before the $r$-th success in independent Bernoulli trials.
    - **pmf**: $P(Y = y | r, p) = \binom{r+y-1}{y} p^r (1-p)^y$ for $y \in {0, 1, \dots }$.
    - **Note**: It is the limit of the Poisson distribution under specific conditions.
- **Geometric Distribution | 几何分布**:
    - **Definition**: A special case of the Negative Binomial where $r=1$.
    - **Memoryless Property | 无记忆性**: For integers $s > t$, $P(X > s | X > t) = P(X > s - t)$.

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

#### 3.4 Exponential Families | 指数族

- **Definition**: A family of distributions is an exponential family if it can be written as $f(x | \theta) = h(x) c(\theta) \exp\left( \sum_{i=1}^k w_i(\theta) t_i(x) \right)$.
- **Support Condition**: The set ${x : f(x | \theta) > 0}$ must not depend on the parameter $\theta$.
- **Natural Parameter Space | 自然参数空间**: The set of values $\eta = (\eta_1, \dots, \eta_k)$ for which the integral of the kernel is finite.
- **Curved Exponential Family | 弯曲指数族**: A family where the dimension of the parameter vector $\theta$ is less than the number of terms $k$ in the exponent.

#### 3.5 Location and Scale Families | 位置与尺度族

- **Standard pdf**: A baseline pdf $f(x)$ from which other members of the family are generated via transformation.
- **Location Family | 位置族**: Formed by shifting: $f(x - \mu)$.
- **Scale Family | 尺度族**: Formed by stretching/contracting: $\frac{1}{\sigma} f(x/\sigma)$.
- **Location-Scale Family | 位置尺度族**: Formed by both: $\frac{1}{\sigma} f\left( \frac{x-\mu}{\sigma} \right)$.

#### 3.6 Inequalities and Identities | 不等式与恒等式

- **Chebychev’s Inequality | 切比雪夫不等式**: For any $r > 0$ and non-negative function $g(x)$, $P(g(X) \ge r) \le \frac{E g(X)}{r}$.
- **Stein’s Lemma | Stein 引理**: If $X \sim n(\theta, \sigma^2)$ and $g$ is differentiable, $E[g(X)(X-\theta)] = \sigma^2 E g'(X)$.
- **Hwang’s Lemma | Hwang 引理**:
    - **Poisson**: $E[\lambda g(X)] = E[X g(X-1)]$.
    - **Negative Binomial**: $E[(1-p) g(X)] = E\left[ \frac{X}{r+X-1} g(X-1) \right]$.

#### 3.8 Miscellanea | 杂项

- **Poisson Postulates**: The Poisson distribution can be derived from assumptions of independent and identically distributed arrivals proportional to time period length.
- **Gauss and Vysochanskiĭ-Petunin Inequalities**: Tighter probability bounds than Chebychev for unimodal distributions.