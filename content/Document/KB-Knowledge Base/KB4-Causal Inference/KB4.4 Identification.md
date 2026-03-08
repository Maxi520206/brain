# [[B20C4-Actions, Plans, and Direct Effects]]
### 4.3 When is the Effect of an Action Identifiable?

- **Core Principle**: Repeated application of $do$-calculus | $do$ 演算 inference rules can reduce $P(y | do(x))$ to a "hat-free" (interventional-free) expression.

#### 4.3.1 Graphical Conditions for Identification

- **Sufficient Conditions**: Four graphical conditions exist for the identifiability of $P(y | do(x))$ when $X$ and $Y$ are single variables.
    1. No back-door path from $X$ to $Y$ in $G$.
    2. No directed path from $X$ to $Y$ in $G$.
    3. A set of nodes $B$ exists that blocks all back-door paths from $X$ to $Y$ such that $P(b | do(x))$ is identifiable.
    4. Sets $Z_1$ and $Z_2$ exist where $Z_1$ blocks directed paths and $Z_2$ blocks back-door paths.

#### 4.3.2 Remarks on Efficiency

- **Minimal Set Testing**: Testing Condition 3 with a single minimal blocking set $B$ is sufficient to determine identifiability.
- **Tractability**: Pruning the search space renders the test for these conditions computationally practical.

#### 4.3.3 Deriving a Closed-Form Expression for Control Queries

- **Function `ClosedForm`**: An algorithm that either determines non-identifiability or provides the closed-form expression for $P(y | do(x))$ in terms of observed distributions.

### 4.4 The Identification of Dynamic Plans

- **Sequential Plan | 序列计划**: A sequence of time-varying actions designed to produce an outcome, where actions may be influenced by prior observations.

#### 4.4.1 Motivation

- **Confounding Complexity**: Plans involve confounders that are themselves affected by previous control variables.
- **Caution**: Adjusting for variables on a causal pathway between action and consequence is generally shunned as it interferes with the total effect estimate.

#### 4.4.2 Plan Identification: Notation and Assumptions

- **Control Variables**: Ordered sequence $X = X_1, X_2, \dots, X_n$ where $X_k$ is a nondescendant of $X_{k+j}$.
- **Goal**: Evaluate the impact of plan $\hat{x} = (\hat{x}_1, \dots, \hat{x}_n)$ on outcome $Y$.

#### 4.4.3 Plan Identification: The Sequential Back-Door Criterion

- **Sequential Back-Door Criterion | 序列 Back-door 准则**: The probability $P(y | \hat{x}_1, \dots, \hat{x}_n)$ is identifiable if, for every $k$, a set $Z_k$ exists satisfying specific nondescendant and $d$-separation conditions.
- **Formula**: $$P(y | \hat{x}_1, \dots, \hat{x}_n) = \sum_{z_1, \dots, z_n} P(y | z_1, \dots, z_n, x_1, \dots, x_n) \prod_{k=1}^n P(z_k | z_1, \dots, z_{k-1}, x_1, \dots, x_{k-1})$$.
- **G-identifiability**: Any expression identifiable by this criterion is termed G-identifiable.