
### 1.1 Introduction to Probability Theory

### 1.1.1 Why Probabilities?

- **Accommodating Uncertainty | 容忍不确定性**: Causal utterances like "reckless driving causes accidents" imply that antecedents make consequences more likely rather than absolutely certain.
- **Standard Mathematical Language**: Probability theory serves as the official language for causal modeling in economics, epidemiology, sociology, and psychology.
- **Tolerating Exceptions | 容忍例外**: Probability theory can handle unexplicated exceptions (e.g., a roof gets wet unless covered by plastic) without creating logical paradoxes.
- **Universality**: Portraying causal problems in probabilistic language emphasizes their universality across different scientific domains.

### 1.1.3 Combining Predictive and Diagnostic Supports

- **Bayes's Rule Formulation | 贝叶斯法则**: The posterior odds $O(H|e)$ are the product of prior odds $O(H)$ and the likelihood ratio $L(e|H)$.
- **Predictive Support | 预测性支持**: Represented by the prior odds $O(H)$, which measures the support given to a hypothesis by background knowledge alone.
- **Diagnostic Support | 诊断性支持**: Represented by the likelihood ratio $L(e|H)$, measuring the retrospective support given to a hypothesis by observed evidence.
- **Modularity | 模块化**: The relationship $P(e|H)$ (e.g., symptom given disease) is often local and stable, remaining invariant regardless of other rules or changes in the knowledge base, such as an epidemic.

---

### 1.2 Graphs and Probabilities

### 1.2.1 Graphical Terminology

- **Directed Acyclic Graph (DAG) | 有向无环图**: A directed graph containing no directed cycles.
- **Kinship Relations | 亲属关系**: Uses terms like parents | 父母, children | 子女, ancestors | 祖先, and descendants | 后裔 to describe node relationships along directed edges.
- **Family | 家族**: A set of nodes consisting of a node and all its parents.

### 1.2.2 Bayesian Networks

- **Definition**: A DAG that acts as a carrier of conditional independence relationships.
- **Chain Rule Decomposition**: Every distribution $P$ on $n$ variables can be decomposed into a product of conditional distributions: $P(x_1, \dots, x_n) = \prod_j P(x_j | pa_j)$, where $pa_j$ are the values of the parents of $X_j$.

### 1.2.3 d-Separation and Observational Equivalence

- **d-Separation Criterion**: A graphical test to determine conditional independence between sets of variables.
- **Observational Equivalence | 观测等价性**: Two DAGs are equivalent if and only if they share the same skeletons and the same sets of v-structures (converging arrows with unconnected tails).
- **Limits of Inference**: Observationally equivalent networks cannot be distinguished using probabilistic data alone without temporal information or experimental manipulation.

---

### 1.3 Causal Bayesian Networks

### 1.3.1 Causal Networks as Oracles for Interventions

- **Principle of Autonomy | 自主性原则**: Assumes that each parent-child relationship represents a stable and autonomous physical mechanism that can be changed without affecting others.
- **Predicting Intervention Effects**: Causal models predict how probabilities change due to external interventions (e.g., policy changes), a task impossible with joint distributions alone.
- **Truncated Factorization | 截断因子分解**: The interventional distribution $P_x(v)$ resulting from $do(X=x)$ is computed by removing the factors $P(x_i | pa_i)$ for all $X_i \in X$ from the joint distribution product.

### 1.3.2 Causal Relationships and Their Stability

- **Ontological Stability | 本体稳定性**: Causal relationships describe objective physical constraints and remain unaltered even if knowledge about the environment changes.
- **Robustness to Change**: Causal relations are invariant to changes in the mechanisms governing other variables, unlike probabilistic associations which vary based on what is known or observed.

---

### 1.4 Functional Causal Models

### 1.4.1 Structural Equations

- **Definition**: Deterministic functional equations of the form $x_i = f_i(pa_i, u_i)$, where $pa_i$ are immediate causes and $u_i$ are omitted factors (disturbances).
- **Laplacian Conception | 拉普拉斯观**: Nature's laws are deterministic, and randomness surfaces only due to ignorance of underlying boundary conditions.
- **Recipe Metaphor**: A structural equation is a "recipe" or "law" specifying the value nature assigns to $X_i$ for every possible combination of its parents and disturbances.

### 1.4.2 Probabilistic Predictions in Causal Models

- **Causal Markov Condition | 因果马尔可夫条件**: Every Markovian causal model induces a distribution where each variable is independent of its nondescendants given its parents. ^1632d9
- **Common-Cause Assumption**: Dependence between any two variables implies one causes the other or a third variable causes both.
- **Judgmental Advantages**: Assumptions of conditional independence are easier to judge in functional models because they are cast as judgments about the presence or absence of unobserved common causes.

### 1.4.4 Counterfactuals in Functional Models

- **Structural Interpretation | 结构化解释**: The potential response $Y_x(u)$ is the unique solution for $Y$ in a submodel $M_x$ where the equations for $X$ are replaced by $X=x$.
- **The Three-Step Procedure**:
    1. **Abduction | 溯因**: Update the probability $P(u)$ of the error terms given the evidence $e$.
    2. **Action | 行动**: Simulate the intervention $do(X=x)$ by modifying the model equations.
    3. **Prediction | 预测**: Use the modified model to compute the probability of the outcome $Y$.

---

### 1.5 Causal Versus Statistical Terminology

### 1.5.1 Parameters and Assumptions

- **Statistical Parameter | 统计参数**: Any quantity defined in terms of a joint probability distribution of observed variables (e.g., conditional expectation $E(Y|x)$).
- **Causal Parameter | 因果参数**: Any quantity defined in terms of a causal model that is not a statistical parameter.
- **Statistical Assumption | 统计假设**: A constraint on the joint distribution, such as the Markov condition.
- **Causal Assumption | 因果假设**: A constraint on the causal model that cannot be realized by statistical assumptions alone (e.g., that $u_i$ and $u_j$ are uncorrelated).

### 1.5.2 Concept Demarcation

- **Statistical Concepts**: Correlation, regression, likelihood, risk ratio, propensity score.
- **Causal Concepts**: Randomization, influence, effect, confounding, intervention, explanation.
- **The Notational Barrier**: Standard probability calculus (using expectation and conditionalization) is insufficient for expressing causal assumptions; new notation like the $do$-operator is required to distinguish causal dependence from statistical dependence.