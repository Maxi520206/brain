
#### 2.1 Distributions of Functions of a Random Variable | 随机变量函数的分布

- **Concept | 概念**: If $X$ is a random variable with cdf $F_X(x)$, then any function $Y = g(X)$ is also a random variable.
- **Support Set | 支撑集**: Defined as $\mathcal{X} = {x: f_X(x) > 0}$ and $\mathcal{Y} = {y: y = g(x) \text{ for some } x \in \mathcal{X}}$.
- **Cdf Method | 累积分布函数法**:
    - $F_Y(y) = P(g(X) \le y) = \int_{{x: g(x) \le y}} f_X(x) dx$.
- **Transformation Theorem (Monotone Case) | 变换定理（单调情况）**:
    - **Theorem**: Let $X$ have pdf $f_X(x)$ and $Y = g(X)$ where $g$ is monotone. The pdf of $Y$ is: $$f_Y(y) = f_X(g^{-1}(y)) \left| \frac{d}{dy} g^{-1}(y) \right|$$ for $y \in \mathcal{Y}$.
    - **Notes**: $g$ must be one-to-one and onto from $\mathcal{X}$ to $\mathcal{Y}$.
- **Piecewise Monotone Case | 分段单调情况**:
    - If $g(x)$ is not monotone, partition $\mathcal{X}$ into $A_1, \dots, A_k$ where $g$ is monotone.
    - **Theorem**: $f_Y(y) = \sum_{i=1}^k f_X(g_i^{-1}(y)) \left| \frac{d}{dy} g_i^{-1}(y) \right|$.
- **Probability Integral Transformation | 概率积分变换**:
    - If $X$ has a continuous cdf $F_X(x)$, then $Y = F_X(X) \sim \text{Uniform}(0,1)$.
    - **Application**: Used for generating samples from a specific distribution $F_X$ by transforming a Uniform sample $U$ via $F_X^{-1}(U)$.

#### 2.2 Expected Values | 期望值

- **Definition | 定义**: The expected value of $g(X)$ is the average value weighted by the probability distribution.
    - Continuous: $E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x) dx$.
    - Discrete: $E[g(X)] = \sum_{x \in \mathcal{X}} g(x) f_X(x)$.
- **Existence**: $E[g(X)]$ exists if $E|g(X)| < \infty$. Otherwise, it is said not to exist.
- **Properties | 性质**:
    - **Linearity | 线性**: $E[a g_1(X) + b g_2(X) + c] = a E[g_1(X)] + b E[g_2(X)] + c$.
    - **Monotonicity | 单调性**: If $g_1(x) \ge g_2(x)$, then $E[g_1(X)] \ge E[g_2(X)]$.
- **Minimizing Distance | 距离最小化**: The value $b$ that minimizes $E(X-b)^2$ is $b = EX$.

#### 2.3 Moments and Moment Generating Functions | 矩与矩生成函数

- **Moments | 矩**:
    - **$n$-th moment | $n$ 阶矩**: $\mu'_n = E X^n$.
    - **$n$-th central moment | $n$ 阶中心矩**: $\mu_n = E(X - \mu)^n$, where $\mu = E X$.
- **Variance | 方差**:
    - **Definition**: $\text{Var } X = E(X - EX)^2$.
    - **Calculation Formula**: $\text{Var } X = E X^2 - (EX)^2$.
    - **Linear Transformation**: $\text{Var}(aX + b) = a^2 \text{Var } X$.
- **Moment Generating Function (mgf) | 矩生成函数**:
    - **Definition**: $M_X(t) = E e^{tX}$, provided it exists for $t$ in a neighborhood of 0.
    - **Generating Moments**: $E X^n = M_X^{(n)}(0)$ ($n$-th derivative at $t=0$).
- **Uniqueness and Characterization | 唯一性与刻画**:
    - The mgf uniquely determines the distribution if it exists in a neighborhood of 0.
    - **Caution**: Bounded support distributions are uniquely determined by their moments, but unbounded ones (like Lognormal) may not be.
- **Convergence Property | 收敛性质**: Convergence of mgfs in a neighborhood of 0 implies convergence of the corresponding cdfs.
- **Mgf Transformation**: $M_{aX+b}(t) = e^{bt} M_X(at)$.

#### 2.4 Differentiating under an Integral Sign | 积分号下求导

- **Condition | 条件**: Interchanging the order of integration and differentiation is legitimate under specific conditions (Leibniz's Rule).
- **Recursion Relation | 递归关系**: Often used to derive higher moments. For $X \sim \text{Exponential}(\lambda)$, $E X^{n+1} = \lambda E X^n + \lambda^2 \frac{d}{d\lambda} E X^n$.