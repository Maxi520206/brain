# [[B71C9-Interval Estimation]]
#### 9.1 Introduction | 引言
- **Interval Estimate | 区间估计** (Definition 9.1.1): A pair of functions $L(x_1, \dots, x_n)$ and $U(x_1, \dots, x_n)$ such that $L(x) \le U(x)$ for all sample points $x$. The realized values $[L(x), U(x)]$ form the interval estimate.
- **Precision vs. Confidence | 精确度与置信度**: By moving from a point estimate to an interval, an experimenter sacrifices precision but gains Confidence | 置信度—the assurance that the assertion is correct.
- **Coverage Probability | 覆盖概率** (Definition 9.1.4): The probability that the random interval $[L(X), U(X)]$ covers the true parameter $\theta$, denoted as $P_\theta(\theta \in [L(X), U(X)])$.
- **Confidence Coefficient | 置信系数** (Definition 9.1.5): The infimum of the coverage probability over the entire parameter space: $$\inf_\theta P_\theta(\theta \in [L(X), U(X)])$$.
#### 9.2.1 Inverting a Test Statistic | 翻转测试统计量

- **Core Principle**: There is a one-to-one correspondence between every confidence set and a family of hypothesis tests.
- **Theorem 9.2.2**:
    - Let $A(\theta_0)$ be the acceptance region of a level $\alpha$ test for $H_0: \theta = \theta_0$.
    - For each sample point $x$, define a set in the parameter space: $C(x) = {\theta_0: x \in A(\theta_0)}$.
    - The random set $C(X)$ is a $1-\alpha$ Confidence Set | 置信集.
- **Logical Link**: The connection is maintained by the tautology: $x \in A(\theta_0) \iff \theta_0 \in C(x)$.
- **Structural Effects**: One-sided tests typically invert to one-sided intervals (e.g., upper/lower bounds), and two-sided tests yield two-sided intervals.
- **Sufficiency Principle**: When constructing sets via inversion, one can restrict attention to sufficient statistics to find good confidence sets.
###### A1-W10-D4
> Confidence Interval Derivation
> 
> From CLT:
> (X̄ − μ)/(σ/√n) ~ N(0,1)
> 
> Using the standard normal property:
> 
> P(-1.96 < Z < 1.96) ≈ 0.95
> 
> This implies:
> 
> P(X̄ − 1.96 σ/√n < μ < X̄ + 1.96 σ/√n) ≈ 0.95
> 
> Thus the 95% confidence interval is:
> 
> X̄ ± 1.96 σ/√n
> 
> Interpretation:
> 
> If the sampling process were repeated many times,
> about 95% of the intervals would contain the true mean μ.