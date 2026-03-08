# [[B70C4-Expectation]]
**Definition of expectation | 期望的定义**

- **Concept | 概念**: A single-number summary describing the "average" value of a random variable.
- **Definition (Discrete) | 定义（离散型）**: For a discrete r.v. $X$ with possible values $x_1, x_2, \dots$: $E(X) = \sum_{j=1}^{\infty} x_j P(X = x_j)$.
- **Theorem | 定理**: For any r.v.s $X, Y$ and constant $c$:
    1. $E(X + Y) = E(X) + E(Y)$
    2. $E(cX) = cE(X)$.
- **Dependency | 依赖性**: Linearity holds even if $X$ and $Y$ are dependent.
- **Monotonicity | 单调性**: If $X \geq Y$ with probability 1, then $E(X) \geq E(Y)$.

**Law of the unconscious statistician (LOTUS) | 无意识统计学家法则**

- **Theorem | 定理**: If $X$ is a discrete r.v. and $g$ is a function: $E(g(X)) = \sum_{x} g(x) P(X = x)$.
- **Significance | 意义**: This allows calculating the expected value of a function of $X$ using only the PMF of $X$, without finding the PMF of $g(X)$ first.

**Variance | 方差**

- **Definition | 定义**: $Var(X) = E((X - E(X))^2) = E(X^2) - (E(X))^2$.
- **Standard Deviation | 标准差**: $SD(X) = \sqrt{Var(X)}$.
- **Properties | 性质**:
    - $Var(X + c) = Var(X)$.
    - $Var(cX) = c^2 Var(X)$.
    - If $X, Y$ independent: $Var(X + Y) = Var(X) + Var(Y)$.
# [[B71C2-Transformations and Expectations]]

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