#### 5.1 Basic Concepts of Random Samples | 随机样本的基本概念

- **Random Sample | 随机样本**: A collection of $n$ independent and identically distributed (iid) random variables $X_1, \dots, X_n$ from a population $f(x)$.
- **Joint PDF/PMF**: The joint density of a random sample is the product of marginal densities: $f(x_1, \dots, x_n) = \prod_{i=1}^{n} f(x_i)$.
- **Finite Population Sampling | 有限总体抽样**:
    - **With Replacement | 有放回抽样**: Results in iid random variables, satisfying the definition of a random sample.
    - **Without Replacement (Simple Random Sampling) | 无放回抽样**: Random variables are not independent; however, they remain identically distributed.

#### 5.2 Sums of Random Variables from a Random Sample | 随机样本随机变量之和

##### Theorem 5.2.6: Properties of the Sample Mean and Variance | 样本均值与方差的性质

Let $X_1, \dots, X_n$ be a random sample from a population with mean $\mu$ and variance $\sigma^2 < \infty$. The following properties hold:

- **Expectation of Sample Mean | 样本均值的期望**: $$E\bar{X} = \mu$$
    - This shows that the sample mean is an **Unbiased Estimator | 无偏估计量** of the population mean.
- **Variance of Sample Mean | 样本均值的方差**: $$Var \bar{X} = \frac{\sigma^2}{n}$$
    - The variance of the sample mean decreases as the sample size $n$ increases, indicating that $\bar{X}$ becomes a more precise estimate of $\mu$ with more data.
- **Expectation of Sample Variance | 样本方差的期望**: $$ES^2 = \sigma^2$$
    - This establishes $S^2$ as an **Unbiased Estimator | 无偏估计量** of the population variance.
- **Significance of the Divisor $n-1$ | 分母 $n-1$ 的意义**:
    - The use of $n-1$ (rather than $n$) in the definition of $S^2$ is specifically required to achieve unbiasedness.
    - If $S^2$ were defined using $n$ as the divisor, the expected value would be $\frac{n-1}{n}\sigma^2$, resulting in a biased estimate.
- **Assumptions | 假设条件**:
    - The proofs for $E\bar{X}$ and $Var\bar{X}$ require only the existence of the population mean and variance.
    - Unlike the results in Section 5.3, these properties **do not** require the population to be normally distributed.

#### 5.3 Sampling from the Normal Distribution | 正态总体抽样

##### 5.3.1 Properties of the Sample Mean and Variance | 样本均值与方差的性质

- **Independence**: For a sample from a $n(\mu, \sigma^2)$ distribution, $\bar{X}$ and $S^2$ are independent random variables.
- **Distribution of Mean**: $\bar{X} \sim n(\mu, \sigma^2/n)$.
- **Distribution of Variance**: $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2_{n-1}$ (Chi-squared distribution with $n-1$ degrees of freedom).

##### 5.3.2 The Derived Distributions: Student’s $t$ and Snedecor’s $F$ | 派生分布：$t$ 分布与 $F$ 分布

- **Student’s $t$ Distribution | $t$ 分布**:
    - **Definition**: If $U \sim n(0,1)$ and $V \sim \chi^2_p$ are independent, then $T = \frac{U}{\sqrt{V/p}}$ follows a $t$ distribution with $p$ d.f..
    - **Statistical Application**: $T = \frac{\bar{X}-\mu}{S/\sqrt{n}} \sim t_{n-1}$.
- **Snedecor’s $F$ Distribution | $F$ 分布**:
    - **Definition**: If $U \sim \chi^2_p$ and $V \sim \chi^2_q$ are independent, then $F = \frac{U/p}{V/q}$ follows an $F$ distribution with $(p, q)$ d.f..
    - **Statistical Application**: Used for comparing two independent sample variances: $\frac{S_X^2/\sigma_X^2}{S_Y^2/\sigma_Y^2} \sim F_{n-1, m-1}$.

#### 5.4 Order Statistics | 次序统计量

- **Definition**: The sample values placed in ascending order: $X_{(1)} \le X_{(2)} \le \dots \le X_{(n)}$.
- **Sample Range | 样本极差**: $R = X_{(n)} - X_{(1)}$.
- **Sample Median | 样本中位数**: The middle observation(s) in the ordered sample.
- **Pdf of the $j$-th Order Statistic**: For a continuous population: $$f_{X_{(j)}}(x) = \frac{n!}{(j-1)!(n-j)!} f_X(x) [F_X(x)]^{j-1} [1-F_X(x)]^{n-j}$$.
- **Joint Pdf of $X_{(i)}$ and $X_{(j)}$**: Provides information on the joint behavior of two order statistics.


#### 5.5 Convergence Concepts | 收敛概念

This section describes the asymptotic behavior of sequences of random variables as the sample size $n \to \infty$.

##### 5.5.1 Convergence in Probability | 依概率收敛

- **Definition | 定义**: A sequence of random variables $X_1, X_2, \dots$ converges in probability to a random variable $X$ if, for every $\epsilon > 0$: $$\lim_{n \to \infty} P(|X_n - X| \ge \epsilon) = 0 \quad \text{or equivalently} \quad \lim_{n \to \infty} P(|X_n - X| < \epsilon) = 1$$
- **Weak Law of Large Numbers (WLLN) | 弱大数定律**: Let $X_1, X_2, \dots$ be i.i.d. random variables with $E X_i = \mu$ and $Var X_i = \sigma^2 < \infty$. The sample mean $\bar{X}_n$ converges in probability to $\mu$: $$\lim_{n \to \infty} P(|\bar{X}_n - \mu| < \epsilon) = 1$$
    - **Proof basis**: Derived via **Chebychev’s Inequality | 切比雪夫不等式**, showing $P(|\bar{X}_n - \mu| \ge \epsilon) \le \frac{\sigma^2}{n\epsilon^2} \to 0$.
- **Consistency | 一致性**: An estimator $W_n$ is a **consistent sequence of estimators | 一致估计序列** if $W_n$ converges in probability to the parameter $\theta$.
- **Theorem 5.5.4**: If $X_n \xrightarrow{P} X$ and $h$ is a continuous function, then $h(X_n) \xrightarrow{P} h(X)$.

##### 5.5.2 Almost Sure Convergence | 几乎处处收敛

- **Definition | 定义**: A sequence $X_1, X_2, \dots$ converges almost surely to $X$ if, for every $\epsilon > 0$: $$P(\lim_{n \to \infty} |X_n - X| < \epsilon) = 1$$
- **Comparison | 比较**: This is a stronger criterion than convergence in probability ($X_n \xrightarrow{as} X \Rightarrow X_n \xrightarrow{P} X$). It corresponds to pointwise convergence on the sample space except for a set of probability zero.
- **Strong Law of Large Numbers (SLLN) | 强大数定律**: For i.i.d. $X_i$ with $E X_i = \mu$ and $Var X_i = \sigma^2 < \infty$, $\bar{X}_n$ converges almost surely to $\mu$.

##### 5.5.3 Convergence in Distribution | 依分布收敛

- **Definition | 定义**: A sequence $X_1, X_2, \dots$ converges in distribution to $X$ if: $$\lim_{n \to \infty} F_{X_n}(x) = F_X(x)$$ at all points $x$ where $F_X(x)$ is continuous.
- ==**Central Limit Theorem (CLT) | 中心极限定理**==: Let $X_1, X_2, \dots$ be i.i.d. random variables with $E X_i = \mu$ and $0 < Var X_i = \sigma^2 < \infty$. The standardized sample mean converges in distribution to a standard normal: $$\frac{\bar{X}_n - \mu}{\sigma / \sqrt{n}} \xrightarrow{d} n(0, 1)$$
- **Slutsky’s Theorem | Slutsky 定理**: If $X_n \xrightarrow{d} X$ and $Y_n \xrightarrow{P} a$ (a constant), then:
    - $Y_n X_n \xrightarrow{d} aX$
    - $X_n + Y_n \xrightarrow{d} X + a$

##### 5.5.4 The Delta Method | Delta 方法

- **Concept | 概念**: Uses Taylor series expansions to approximate the mean and variance of a function of a random variable, and to obtain its limiting distribution.
- **First-order Delta Method | 一阶 Delta 方法**: If $\sqrt{n}(Y_n - \theta) \xrightarrow{d} n(0, \sigma^2)$ and $g'(\theta)$ exists and is non-zero, then: $$\sqrt{n}[g(Y_n) - g(\theta)] \xrightarrow{d} n(0, \sigma^2 [g'(\theta)]^2)$$
- **Second-order Delta Method | 二阶 Delta 方法**: If $g'(\theta) = 0$ and $g''(\theta) \ne 0$, then: $$n[g(Y_n) - g(\theta)] \xrightarrow{d} \sigma^2 \frac{g''(\theta)}{2} \chi^2_1$$
- **Multivariate Delta Method | 多维 Delta 方法**: Generalizes the result to a vector of statistics $\bar{\mathbf{X}} = (\bar{X}_1, \dots, \bar{X}_p)$ using the gradient and covariance matrix: $$\sqrt{n}[g(\bar{\mathbf{X}}) - g(\boldsymbol{\mu})] \xrightarrow{d} n(0, \tau^2), \quad \text{where } \tau^2 = \sum_i \sum_j \sigma_{ij} \frac{\partial g(\boldsymbol{\mu})}{\partial \mu_i} \frac{\partial g(\boldsymbol{\mu})}{\partial \mu_j}$$
#### 5.6 Generating a Random Sample | 生成随机样本

- **Probability Integral Transform | 概率积分变换**: Used to generate samples from a cdf $F$ by calculating $F^{-1}(U)$ where $U \sim Uniform(0,1)$.
- **Accept/Reject Algorithm | 接受-拒绝算法**: A method to generate random variables from a target density $f$ using a candidate density $g$.
- **Box-Muller Transformation**: Specifically used to generate normal random variables from uniform ones.