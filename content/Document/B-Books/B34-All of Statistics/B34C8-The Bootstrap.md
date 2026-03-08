
- **Core Objective | 核心目标**: A method for estimating standard errors and computing confidence intervals for a statistic $T_n = g(X_1, \dots, X_n)$.
- **Two-Step Idea | 两步走思想**:
    1. **Estimation | 估计**: Estimate the variance $V_F(T_n)$ using the plug-in version $V_{\hat{F}_n}(T_n)$, where $\hat{F}_n$ is the empirical distribution.
    2. **Simulation | 模拟**: Approximate $V_{\hat{F}_n}(T_n)$ using simulation when a simple formula is unavailable.

#### 8.1 Simulation | 模拟

- **Mechanism | 机制**: Suppose we draw an IID sample $Y_1, \dots, Y_B$ from a distribution $G$. According to the Law of Large Numbers (LLN), as $B \to \infty$:
    - $\bar{Y}_n = \frac{1}{B} \sum_{j=1}^B Y_j \xrightarrow{P} E(Y)$.
    - The sample variance of simulated values $\frac{1}{B} \sum_{j=1}^B (Y_j - \bar{Y}_n)^2$ converges to $V(Y)$.
- **Utility | 用途**: Allows approximating expectations and variances of any function $h(Y)$ by taking large $B$.

#### 8.2 Bootstrap Variance Estimation | Bootstrap 方差估计

- **Conceptual Mapping | 概念映射**:
    - **Real World | 现实世界**: $F \Rightarrow X_1, \dots, X_n \Rightarrow T_n = g(X_1, \dots, X_n)$.
    - **Bootstrap World | Bootstrap 世界**: $\hat{F}_n \Rightarrow X_1^*, \dots, X_n^* \Rightarrow T_n^* = g(X_1^*, \dots, X_n^*)$.
- **Resampling | 重采样**: Drawing an observation from $\hat{F}_n$ is equivalent to drawing one point at random from the original data set **with replacement**.
- **Algorithm | 算法步骤**:
    1. Draw $n$ observations with replacement from data to get $X_1^*, \dots, X_n^* \sim \hat{F}_n$.
    2. Compute $T_n^* = g(X_1^*, \dots, X_n^*)$.
    3. Repeat steps 1 and 2, $B$ times, to get $T_{n,1}^*, \dots, T_{n,B}^*$.
    4. Calculate the bootstrap variance: $$v_{boot} = \frac{1}{B} \sum_{b=1}^B \left( T_{n,b}^* - \frac{1}{B} \sum_{r=1}^B T_{n,r}^* \right)^2$$
- **Note | 注释**: The bootstrap standard error is $se = \sqrt{v_{boot}}$.

#### 8.3 Bootstrap Confidence Intervals | Bootstrap 置信区间

1. **Method 1: The Normal Interval | 正态区间**:
    - **Formula | 公式**: $T_n \pm z_{\alpha/2} \widehat{se}_{boot}$.
    - **Constraint | 限制**: Only accurate if the distribution of $T_n$ is close to Normal.
2. **Method 2: Pivotal Intervals | 枢轴区间**:
    - **Pivot | 枢轴量**: $R_n = \hat{\theta}_n - \theta$.
    - **Construction | 构建**: Let $H(r)$ be the CDF of the pivot. The $1-\alpha$ interval is $C_n = (\hat{a}, \hat{b})$: $$\hat{a} = 2\hat{\theta}_n - \theta^*_{1-\alpha/2}, \quad \hat{b} = 2\hat{\theta}_n - \theta^*_{\alpha/2}$$
    - where $\theta^*_\beta$ is the $\beta$ sample quantile of the bootstrap replications.
3. **Method 3: Percentile Intervals | 分位数区间**:
    - **Definition | 定义**: $C_n = (\theta^*_{\alpha/2}, \theta^*_{1-\alpha/2})$.
    - **Justification | 理由**: Assumes there exists a monotone transformation that makes the distribution Normal.

#### 8.4 Bibliographic Remarks | 文献评注

- **Origins | 起源**: The bootstrap was invented by Bradley Efron in 1979.

#### 8.5 Appendix | 附录

##### 8.5.1 The Jackknife | 刀切法

- **Definition | 定义**: A method for computing standard errors by removing one observation at a time.
- **Formula | 公式**: Let $T_{(-i)}$ be the statistic computed without the $i$-th observation. $$v_{jack} = \frac{n-1}{n} \sum_{i=1}^n (T_{(-i)} - \bar{T}_n)^2$$
- **Pros/Cons | 优缺点**: Less computationally expensive than bootstrap but less general; fails for sample quantiles (like the median).

##### 8.5.2 Justification For The Percentile Interval | 分位数区间的证明

- **Transformation | 变换**: Based on the assumption that a monotone transformation $U = m(T)$ exists such that $U \sim N(\phi, c^2)$.
- **Result | 结果**: If such a transformation exists (even if unknown), the percentile interval achieves approximately $1-\alpha$ coverage.
###### A1-W10-D5
>Bootstrap is based on the plug-in principle.
>
>Since the true distribution F is unknown, we approximate it using the empirical distribution F̂.
>
>By repeatedly resampling from F̂ and recomputing the statistic, we approximate the sampling distribution of the estimator.