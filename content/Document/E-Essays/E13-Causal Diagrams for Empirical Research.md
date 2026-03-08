- **Keywords**: Causal Inference | 因果推断, Directed Acyclic Graphs | 有向无环图, Confounding Bias | 混淆偏差, Identifiability | 可辨识性, do-calculus | 干预演算.
- **Reference**:
    - **Rosenbaum, P. & Rubin, D. (1983). _The central role of propensity score in observational studies for causal effects_.**
        - Defined the "ignorability" condition (conditional independence of treatment and potential outcomes) which Pearl's graphical criteria operationalize.
    - **Wright, S. (1921). _Correlation and causation_.**
        - Introduced path analysis and the use of diagrams to represent structural relations in biology and economics.
    - **Robins, J. M. (1986). _A new approach to causal inference in mortality studies..._.**
        - Proposed the G-computation formula, a precursor to the identification formulas developed here for longitudinal data.

---

### 1. INTRODUCTION

- **The Challenge**: Traditional statistics lacks a formal language to distinguish between "observing" a variable and "setting" its value.
- **The Soil Fumigant Example**:
    - Soil fumigants ($X$) affect yields ($Y$) through eelworm population ($Z$), but both are confounded by an unobserved last year's population ($Z_0$).
    - Randomized experiments are often infeasible; researchers must rely on qualitative domain knowledge (the diagram).
- **Core Objective**: Provide a principled, nonparametric framework to:
    - Explicate model assumptions.
    - Decide if causal effects are Identifiable | 可辨识 from nonexperimental data.
    - Provide a closed-form mathematical expression for the causal effect.

### 2. GRAPHICAL MODELS AND THE MANIPULATIVE ACCOUNT OF CAUSATION

- **2.1 Graphs and conditional independence**
    - **Recursive Product Decomposition**: $pr(x_1, \dots, x_n) = \prod pr(x_i | pa_i)$.
    - **d-separation | d-分离**: A graphical criterion where a set of nodes $Z$ blocks every path between $X$ and $Y$. If $Z$ d-separates $X$ and $Y$, then $X \perp Y | Z$ in the distribution.
- **2.2 Graphs as models of interventions**
    - **Nonparametric Structural Equations**: Each variable $X_i$ is a deterministic function of its parents and a noise term: $X_i = f_i(pa_i, \epsilon_i)$.
    - **Atomic Intervention | 原子干预**: Denoted as $set(X_i = x_i)$ (or $\hat{x}i$_). This operation "wipes out" the equation for $X_i$ and replaces it with a constant, resulting in a "manipulated graph" $G{\underline{X}}$_.
    - **Causal Effect | 因果效应**: The distribution $pr(y | \hat{x})$ induced by this intervention.

### 3. CONTROLLING CONFOUNDING BIAS

- **3.1 The back-door criterion | 后门准则**
    - A set $Z$ is sufficient for adjustment if:
        1. No node in $Z$ is a descendant of $X$.
        2. $Z$ blocks every path between $X$ and $Y$ that contains an arrow into $X$ (back-door paths).
    - **Adjustment Formula**: $pr(y | \hat{x}) = \sum_z pr(y | x, z) pr(z)$.
- **3.2 The front-door criteria | 前门准则**
    - Applicable when $X$ and $Y$ are confounded by unobservables, but a mediator $Z$ exists such that:
        1. $Z$ intercepts all directed paths from $X$ to $Y$.
        2. There is no unblocked back-door path between $X$ and $Z$.
        3. All back-door paths between $Z$ and $Y$ are blocked by $X$.
    - **Formula**: $pr(y | \hat{x}) = \sum_z pr(z | x) \sum_{x'} pr(y | x', z) pr(x')$.

### 4. A CALCULUS OF INTERVENTION (do-calculus)

- **4.3 Inference Rules**
    - **Rule 1 (Insertion/deletion of observations)**: $pr(y | \hat{x}, z, w) = pr(y | \hat{x}, w)$ if $Y \perp Z | X, W$ in $G_{\bar{X}}$.
    - **Rule 2 (Action/observation exchange)**: $pr(y | \hat{x}, \hat{z}, w) = pr(y | \hat{x}, z, w)$ if $Y \perp Z | X, W$ in $G_{\bar{X}\underline{Z}}$.
    - **Rule 3 (Insertion/deletion of actions)**: $pr(y | \hat{x}, \hat{z}, w) = pr(y | \hat{x}, w)$ if $Y \perp Z | X, W$ in $G_{\bar{X}, \bar{Z}(W)}$.
- **4.5 Surrogate Experiments | 替代实验**: Conditions under which we can estimate the effect of $X$ on $Y$ by intervening on a different variable $Z$ (e.g., controlling diet instead of cholesterol).

### 5. GRAPHICAL TESTS OF IDENTIFIABILITY

- **5.1 General**
    - **Bow-pattern | 弓形结构**: A confounding arc (unobserved common cause) between $X$ and its immediate child on the path to $Y$ generally prevents identification in nonparametric models.
- **5.2 Identifying vs. Nonidentifying Models**
    - Identifiability depends on the graph topology, not the specific functional forms.
    - Adding mediating variables can assist identifiability; adding confounding arcs can only impede it.

---

# Summary and Evaluation

### (1) Research Problem

- **Motivation**: To provide a rigorous mathematical foundation for causal reasoning that traditional probability theory (which lacks an "intervention" operator) cannot support.
- **Claimed Contribution**:
    1. Introduction of the "check" (do) notation for interventions.
    2. The **Back-door** and **Front-door** criteria for identifiability.
    3. A complete **Symbolic Calculus** (do-calculus) for transforming interventional distributions into observational ones.
- **Implicit Assumption**: The existence of a Directed Acyclic Graph (DAG) that accurately represents all relevant causal mechanisms and unobserved confounders.

### (2) Core Idea

- Causal inference is treated as a problem of **Graph Surgery**: intervening on a variable is equivalent to cutting the incoming edges to that node in the diagram and observing the resulting distribution.

### (3) Experiments

- **What is actually tested?** The paper is a theoretical derivation. It uses "thought experiments" (e.g., soil fumigants, smoking and tar) to show that the calculus produces results consistent with intuition but more formally grounded.
- **Does experiment logically support the claim?** Yes, the symbolic derivations (e.g., for the front-door formula) provide a proof-of-concept for the rules of do-calculus.

### (4) Limitations

- **Stated Limitations**:
    - Causal results are only as good as the graph assumptions.
    - Assumes infinite sample size (ignoring sampling variability).
- **Unstated Weakness**: The complexity of identifying whether a variable is a "descendant" or "ancestor" in very large, complex systems may be high for human researchers.
- **Boundary Conditions**: The calculus assumes **Acyclic** models. While mentioned as extendable to cyclic models, the specific rules for feedback loops are not fully detailed here.

---

<aside> 💡

### Constructive Questions

1. **Selection of Covariates**: In practice, how should a researcher decide which unobserved variables are critical enough to be included as "latent nodes" (dashed arcs) versus those that can be safely ignored as part of the noise term $\epsilon$?
2. **Computational Complexity**: For a graph with thousands of nodes, is there an efficient algorithmic implementation to determine if an arbitrary $pr(y | \hat{x})$ is identifiable using these three rules?
3. **Falsifiability**: Since the paper admits identification relies on the graph, what are the most robust ways to use statistical data to _refute_ a proposed causal diagram? </aside>