# [[B71C5-Properties of a Random Sample]]
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
###### A1-W10-D3 $$Var \bar{X}$$

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
