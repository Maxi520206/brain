#### 9.1 Introduction | 引言

- **Set Estimation | 集合估计**: Unlike point estimation which guesses a single value, set estimation asserts that the parameter $\theta$ belongs to a specific subset $C$ of the parameter space $\Theta$.
- **Interval Estimate | 区间估计** (Definition 9.1.1): A pair of functions $L(x_1, \dots, x_n)$ and $U(x_1, \dots, x_n)$ such that $L(x) \le U(x)$ for all sample points $x$. The realized values $[L(x), U(x)]$ form the interval estimate.
- **Interval Estimator | 区间估计量**: The random interval $[L(X), U(X)]$ whose endpoints are random variables.
- **One-sided Intervals | 单侧区间**: Estimates can be formulated as $(-\infty, U(x)]$ (upper bound) or $[L(x), \infty)$ (lower bound).
- **Precision vs. Confidence | 精确度与置信度**: By moving from a point estimate to an interval, an experimenter sacrifices precision but gains Confidence | 置信度—the assurance that the assertion is correct.
- **Coverage Probability | 覆盖概率** (Definition 9.1.4): The probability that the random interval $[L(X), U(X)]$ covers the true parameter $\theta$, denoted as $P_\theta(\theta \in [L(X), U(X)])$.
- **Confidence Coefficient | 置信系数** (Definition 9.1.5): The infimum of the coverage probability over the entire parameter space: $$\inf_\theta P_\theta(\theta \in [L(X), U(X)])$$.
- **Statistical Interpretation**:
    - The interval is the random entity, not the parameter $\theta$.
    - In the frequentist sense, $\theta$ is fixed, and probability statements refer to the random sample $X$.
    - A $1-\alpha$ Confidence Set | 置信集 is one where the confidence coefficient is $1-\alpha$.
- **Variation in Coverage**: Coverage probability may be constant across all $\theta$ or vary with the parameter. If it varies, the guaranteed coverage is the confidence coefficient (the minimum possible probability).
- **Scale Uniform Example**: For a $Uniform(0, \theta)$ population, the interval based on the pivot $Y/\theta$ (where $Y$ is the maximum) provides constant coverage, whereas an additive interval $[Y+c, Y+d]$ has a confidence coefficient of zero because coverage probability drops as $\theta \to \infty$.

### 9.2 Methods of Finding Interval Estimators | 寻找区间估计量的方法

- **Operational Context**: Most functional methods for finding interval estimators are based on the strategy of inverting a test statistic.
- **Methodological Split**: Procedures in sections 9.2.1 through 9.2.3 are frequentist inversions, while Bayesian intervals (9.2.4) rely on a distinct construction based on posterior distributions.

#### 9.2.1 Inverting a Test Statistic | 翻转测试统计量

- **Core Principle**: There is a one-to-one correspondence between every confidence set and a family of hypothesis tests.
- **Theorem 9.2.2**:
    - Let $A(\theta_0)$ be the acceptance region of a level $\alpha$ test for $H_0: \theta = \theta_0$.
    - For each sample point $x$, define a set in the parameter space: $C(x) = {\theta_0: x \in A(\theta_0)}$.
    - The random set $C(X)$ is a $1-\alpha$ Confidence Set | 置信集.
- **Logical Link**: The connection is maintained by the tautology: $x \in A(\theta_0) \iff \theta_0 \in C(x)$.
- **Structural Effects**: One-sided tests typically invert to one-sided intervals (e.g., upper/lower bounds), and two-sided tests yield two-sided intervals.
- **Sufficiency Principle**: When constructing sets via inversion, one can restrict attention to sufficient statistics to find good confidence sets.

#### 9.2.2 Pivotal Quantities | 枢轴量

- **Definition 9.2.6**: A random variable $Q(X, \theta)$ is a Pivotal Quantity | 枢轴量 if its distribution is independent of all unknown parameters.
- **Location-Scale Examples**:
    - **Location Family | 位置族**: $X - \mu$ is pivotal for pdfs of form $f(x-\mu)$.
    - **Scale Family | 尺度族**: $X/\sigma$ is pivotal for pdfs of form $\frac{1}{\sigma}f(x/\sigma)$.
    - **Location-Scale Family | 位置尺度族**: $\frac{\bar{X}-\mu}{S/\sqrt{n}}$ follows Student's $t$-distribution, which is independent of both $\mu$ and $\sigma$.
- **Construction Method**:
    1. Find constants $a, b$ (independent of $\theta$) such that $P_\theta(a \le Q(X, \theta) \le b) \ge 1-\alpha$.
    2. The confidence set is $C(x) = {\theta : a \le Q(x, \theta) \le b}$.
- **Monotonicity Condition**: If $Q(x, \theta)$ is a monotone function of $\theta$ for each $x$, the resulting confidence set $C(x)$ is guaranteed to be an interval.

#### 9.2.3 Pivoting the CDF | 枢轴化累积分布函数

- **Basis**: This method is entirely general and uses the Probability Integral Transformation | 概率积分变换, where $F_T(T|\theta) \sim Uniform(0,1)$ for a continuous statistic $T$.
- **Theorem 9.2.12 (Continuous Case)**: Let $\alpha_1 + \alpha_2 = \alpha$.
    - **Stochastically Increasing Case**: If $F_T(t|\theta)$ is a decreasing function of $\theta$ for each $t$:
        - Define $\theta_U(t)$ such that $F_T(t|\theta_U) = \alpha_1$.
        - Define $\theta_L(t)$ such that $F_T(t|\theta_L) = 1 - \alpha_2$.
        - $[\theta_L(T), \theta_U(T)]$ is a $1-\alpha$ interval.
- **Theorem 9.2.14 (Discrete Case)**: To account for jumps in the CDF, the endpoints for stochastically increasing $T$ are defined by $P(T \le t|\theta_U) = \alpha_1$ and $P(T \ge t|\theta_L) = \alpha_2$.

#### 9.2.4 Bayesian Intervals | 贝叶斯区间

- **Terminology**: Bayesian set estimates are known as Credible Sets | 可信集.
- **Conceptual Difference**: Within the Bayesian framework, $\theta$ is a random variable. One can state that the probability is $1-\alpha$ that $\theta$ is _inside_ a realized interval, which is an invalid statement in frequentist statistics where $\theta$ is fixed.
- **Formal Definition**: For a posterior distribution $\pi(\theta|x)$, a set $A$ has credible probability $1-\alpha$ if $P(\theta \in A | x) = \int_A \pi(\theta|x)d\theta = 1-\alpha$.
- **Mechanism**: Credible sets reflect subjective beliefs updated by data via the posterior distribution.
- **Divergence**: A $1-\alpha$ credible set is not necessarily a $1-\alpha$ confidence set; its classical coverage probability may drop to zero as parameters move toward the boundaries of the support or prior influence.