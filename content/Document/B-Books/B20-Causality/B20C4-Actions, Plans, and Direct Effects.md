<<<<<<< HEAD
### 4.1 Introduction

- **Focus**: Primitive interventions | 原始干预 of the form $do(x)$, representing the setting of variable $X$ to a fixed constant $x$.
- **Purpose of Causal Models**: To facilitate the evaluation of the effects of novel actions and policies that were not anticipated during model construction.

#### 4.1.1 Actions, Acts, and Probabilities

- **Distinction**:
    - **Act | 行为**: The reactive interpretation; viewed from the outside as a consequence of an agent’s beliefs and environment; acts can be predicted.
    - **Action | 行动**: The deliberative interpretation; viewed from the inside as an option of choice in decision-making; actions cannot be predicted.
- **Invariance**: Causal knowledge identifies which elements of the world remain invariant under the action $do(A)$.

#### 4.1.2 Actions in Decision Analysis

- **Traditional Approach**: Attributes the difference between "seeing" and "doing" to differences in total evidence.
- **Influence Diagrams | 影响图 (IDs)**: Each decision variable is represented as an exogenous node, with impacts encoded via conditional probabilities.
- **Limitation**: Advance anticipation and explicit representation of every possible future action are required, making modeling cumbersome.

#### 4.1.3 Actions and Counterfactuals

- **Imaging | 映射**: A probability transformation where each excluded state transfers its mass to the "closest" states, contrasting with Bayesian conditioning.
- **Mechanism-Modification | 机制修改**: The structural approach bases interventions on causal mechanisms, capitalizing on the properties of invariance and autonomy.

### 4.2 Conditional Actions and Stochastic Policies

- **Conditional Action | 条件行动**: Interventions of the form "do $x$ if you see $z$".
- **Stochastic Policy | 随机策略**: Interventions of the form "do $x$ with probability $p$ if you see $z$".
- **Identification**: These elaborate interventions can be identified and evaluated through the analysis of primitive interventions.

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

### 4.5 Direct and Indirect Effects

#### 4.5.1 Direct versus Total Effects

- **Total Effect | 总效应**: Measures the overall impact of $X$ on $Y$.
- **Direct Effect | 直接效应**: Measures the sensitivity of $Y$ to $X$ while all other model factors are held fixed, severing indirect causal paths.

#### 4.5.2 Direct Effects, Definition, and Identification

- **Definition**: $P(y | do(x), do(s_{XY}))$ where $S_{XY}$ is the set of all endogenous variables except $X$ and $Y$.
- **Identifiability**: A direct effect is identifiable whenever the effect of the plan corresponding to the parents of $Y$ is identifiable.

#### 4.5.3 Example: Sex Discrimination in College Admission

- **Context**: Analysis of alleged sex bias at Berkeley.
- **Issue**: Adjusting for department choice ($X_2$) is inappropriate for estimating the direct effect if unrecorded aptitude ($U$) affects both career objectives ($Z$) and admission outcome ($Y$).
- **Mechanism**: Correct adjustment requires accounting for career objectives ($Z$) separately for each gender to eliminate spurious associations.

#### 4.5.4 Natural Direct Effects

- **Natural Direct Effect | 自然直接效应**: The weighted average of controlled direct effects, using the causal effect $P(z | do(x))$ as the weighing function.
- **Applicability**: Identifiable in Markovian models where $do$-operators can be eliminated.

#### 4.5.5 Indirect Effects and the Mediation Formula

- **Natural Indirect Effect | 自然间接效应**: The expected change in $Y$ when $X$ is held constant but mediating variables $Z$ are changed to the values they would have attained under a different $X$.
- **Mediation Formula | 中介公式**: A tool for assessing causal pathways in nonlinear models, enabling the estimation of indirect effects.
=======
### 4.1 Introduction | 引言

- **Core Objective**: To facilitate the evaluation of effects of novel actions and policies that were unanticipated during the construction of the causal model.
- **Fundamental Thesis**: Causal models distinguish between "seeing" (passive observation) and "doing" (external intervention) through local modifications of the graph or structural equations.

#### 4.1.1 Actions, Acts, and Probabilities | 行动、行为与概率

- **Reactive Interpretation (Act | 行为)**:
    - Action as a consequence of an agent’s beliefs and environment.
    - Viewed from the "outside"; can be predicted and serves as evidence for the actor's stimuli.
- **Deliberative Interpretation (Action | 行动)**:
    - Action as an option of choice in contemplated decision making.
    - Viewed from the "inside"; cannot be predicted nor provide evidence.
- **Causal Decision Theory**: Rational agents should act according to theories of actions, demanding action-specific conditionalization (e.g., $do(x)$).

#### 4.1.2 Actions in Decision Analysis | 决策分析中的行动

- **Total Evidence**: Traditional decision theory attributes the difference between seeing and doing to the total evidence available (e.g., observing a barometer vs. setting it).
- **Invariance**: The $do(\cdot)$ operator identifies elements of the world that remain invariant under intervention.

#### 4.1.3 Actions and Counterfactuals | 行动与逆事实

- **Imaging | 镜像法**:
    - A probability transformation used in analyzing subjunctive conditionals.
    - Each excluded state $s$ transfers its probability mass individually to a set of "closest" states $S(s)$.
- **Mechanism-Modification**: The structural approach bases interventions on causal mechanisms, capitalizing on **autonomy** and **invariance**.

---

### 4.2 Conditional Actions and Stochastic Policies | 条件行动与随机策略

- **Conditional Policy (Conditional Action | 条件行动)**:
    - Denoted as $do(X = g(z))$, where variable $X$ responds to a set $Z$ of other variables via a function $g$.
    - **Computation**: $P(y | do(X = g(z))) = \sum_{z} P(y | \hat{x}, z)|_{x=g(z)} P(z)$.
- **Stochastic Policy (Stochastic Policy | 随机策略)**:
    - $X$ is set to $x$ with a certain probability $P^*(x|z)$.
    - **Identification**: Identifying the effect of such policies is equivalent to identifying the expression $P(y | \hat{x}, z)$.

---

### 4.3 When is the Effect of an Action Identifiable? | 何时行动效应是可识别的？

- **General Class**: Characterizes models where repeated application of $do$-calculus rules reduces $P(y|do(x))$ to a "hat-free" expression.

#### 4.3.1 Graphical Conditions for Identification | 识别的图形条件

- **Theorem 4.3.1**: In a semi-Markovian model, $P(y | \hat{x})$ is identifiable if any of the following four conditions hold:
    1. **No back-door path**: $(Y \perp \perp X)_{G_{\underline{X}}}$.
    2. **No directed path**: $(Y \perp \perp X)_{G_{\overline{X}}}$, then $P(y | \hat{x}) = P(y)$.
    3. **Back-door blocking**: There exists a set $B$ such that $(Y \perp \perp X | B)_{G_{\underline{X}}}$ and $P(b | \hat{x})$ is identifiable.
    4. **Mediator set**: There exist sets $Z_1, Z_2$ such that $Z_1$ blocks all directed paths from $X$ to $Y$, and $Z_2$ blocks back-door paths between $Z_1, Y$ and $X, Z_1$.

#### 4.3.2 Remarks on Efficiency | 关于效率的说明

- **Condition 3 Search**: If identification is possible for one minimal set $B_i$, it is identifiable for any other minimal set $B_j$.
- **Condition 4 Search**: The set of children of $X$ intersected with ancestors of $Y$ ($Children(X) \cap Ancestors(Y)$) is a sufficient choice for $Z_1$ if any such set exists.

#### 4.3.3 Deriving a Closed-Form Expression for Control Queries | 导出控制查询的闭式表达式

- **`ClosedForm` Procedure**: A recursive algorithm that tests the four conditions of Theorem 4.3.1 to return either a standard probability expression or `FAIL`.

---

### 4.4 The Identification of Dynamic Plans | 动态计划的识别

- **Dynamic Plan (Dynamic Plan | 动态计划)**: A sequence of time-varying actions designed to produce a specific outcome.

#### 4.4.2 Plan Identification: Notation and Assumptions | 计划识别：符号与假设

- **Variables**: $X = {X_1, \dots, X_n}$ (Control), $Z$ (Covariates), $U$ (Latent), $Y$ (Outcome).
- **Plan ($\hat{x}$)**: An ordered sequence $\hat{x} = (\hat{x}_1, \hat{x}_2, \dots, \hat{x}_n)$.

#### 4.4.3 Plan Identification: The Sequential Back-Door Criterion | 计划识别：序贯后门准则

- **Theorem 4.4.1**: $P(y | \hat{x}_1, \dots, \hat{x}_n)$ is identifiable if for every $1 \leq k \leq n$, there exists a set $Z_k$ such that:
    1. $Z_k \subseteq N_k$ (nondescendants of future actions).
    2. $(Y \perp \perp X_k | X_1, \dots, X_{k-1}, Z_1, \dots, Z_k)_{G_{\underline{X}_k, \overline{X}_{k+1, \dots, n}}}$.
- **G-computation Formula**: $$\sum_{z_1, \dots, z_n} P(y | z_1, \dots, z_n, x_1, \dots, x_n) \prod_{k=1}^n P(z_k | z_1, \dots, z_{k-1}, x_1, \dots, x_{k-1})$$.

#### 4.4.4 Plan Identification: A Procedure | 计划识别：步骤

- **Minimality**: Every choice of a minimal admissible subsequence $Z_1, \dots, Z_k$ is "safe" and will not prevent finding future admissible sets.
- **Order Dependency**: Identifiability may depend on the specific ordering of control variables consistent with the DAG.

---

### 4.5 Direct and Indirect Effects | 直接与间接效应

#### 4.5.1 Direct versus Total Effects | 直接效应 vs 总效应

- **Direct Effect**: Measures sensitivity of $Y$ to $X$ when all other factors in the model are held fixed, severing mediated causal paths.

#### 4.5.2 Direct Effects, Definition, and Identification | 直接效应的定义与识别

- **Definition 4.5.1**: $P(y | do(x), do(s_{XY}))$ where $S_{XY} = V \setminus {X, Y}$.
- **Identification**: The direct effect of $X$ on $Y$ is identifiable whenever the effect of a plan setting all parents of $Y$ ($PA_Y$) is identifiable.

#### 4.5.4 Natural Direct Effects | 天然直接效应

- **Natural Direct Effect (Natural Direct Effect | 天然直接效应)**: The expected change in $Y$ induced by changing $X$ from $x$ to $x'$ while keeping mediating factors constant at the values they **would have obtained** under $do(x)$.
- **Identification**: Valid and identifiable in Markovian models by eliminating all $do$-operators.

#### 4.5.5 Indirect Effects and the Mediation Formula | 间接效应与中介公式

- **Natural Indirect Effect (Natural Indirect Effect | 天然间接效应)**: The expected change in $Y$ by holding $X$ constant ($X=x$) and changing mediators $Z$ to whatever value they would have attained had $X$ been set to $x'$.
- **Mediation Formula**:
    - **Direct Effect**: $DE_{x,x'}(Y) = \sum_{z} [E(Y | x', z) - E(Y | x, z)] P(z | x)$.
    - **Indirect Effect**: $IE_{x,x'}(Y) = \sum_{z} E(Y | x, z) [P(z | x') - P(z | x)]$.
>>>>>>> origin/main
