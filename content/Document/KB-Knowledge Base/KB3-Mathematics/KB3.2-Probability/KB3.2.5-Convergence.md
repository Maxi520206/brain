# [[B71C5-Properties of a Random Sample]]
#### 5.5 Convergence Concepts | 收敛概念

##### 5.5.1 Convergence in Probability | 依概率收敛

- **Definition**: $X_n \xrightarrow{P} X$ if for every $\epsilon > 0$, $\lim_{n \to \infty} P(|X_n - X| \ge \epsilon) = 0$.
- **Weak Law of Large Numbers (WLLN) | 弱大数定律**: The sample mean $\bar{X}_n$ converges in probability to the population mean $\mu$.

##### 5.5.2 Almost Sure Convergence | 几乎处处收敛

- **Definition**: $X_n \xrightarrow{as} X$ if $P(\lim_{n \to \infty} |X_n - X| < \epsilon) = 1$.
- **Strong Law of Large Numbers (SLLN) | 强大数定律**: $\bar{X}_n$ converges almost surely to $\mu$.

##### 5.5.3 Convergence in Distribution | 依分布收敛

- **Definition**: $X_n \xrightarrow{d} X$ if $\lim_{n \to \infty} F_{X_n}(x) = F_X(x)$ at all continuity points of $F_X$.
- ==**Central Limit Theorem (CLT) | 中心极限定理**==: For iid random variables with finite mean $\mu$ and variance $\sigma^2 > 0$, the standardized sample mean $\sqrt{n}(\bar{X}_n - \mu)/\sigma$ converges in distribution to $n(0,1)$.
###### A1-W10-D2 CLT:
> `(X̄ − μ)/(σ/√n) → N(0,1)`
> Standardization:
> 	The sample mean is centered by μ and scaled by σ/√n to converge to a standard normal distribution.
##### 5.5.4 The Delta Method | Delta 方法

- **Theorem**: If $\sqrt{n}(Y_n - \theta) \xrightarrow{d} n(0, \sigma^2)$, then for a differentiable function $g$: $$\sqrt{n}(g(Y_n) - g(\theta)) \xrightarrow{d} n(0, \sigma^2[g'(\theta)]^2)$$.
