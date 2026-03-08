- **Keywords**: Structural Causal Model (SCM) | 结构因果模型, Counterfactuals | 逆事实, Identifiability | 可辨识性, do-calculus | 干预演算, Mediation | 中介分析.
- **Reference**:
    - **Wright, S. (1921). _Correlation and causation_.**
        - Introduced path analysis and the first formal use of diagrams to represent structural relations.,
    - **Neyman, J. (1923). _On the application of probability theory to agricultural experiments_.**
        - Established the foundation of the potential-outcome framework for randomized experiments.,
    - **Rosenbaum, P. & Rubin, D. (1983). _The central role of propensity score in observational studies for causal effects_.**
        - Defined "conditional ignorability" and the use of propensity scores for adjustment.,

---

### 2. Lecture Note: Causal Inference in Statistics

### 1. Introduction

- **Causal vs. Associational Questions**: Most scientific questions (efficacy of drugs, discrimination, policy evaluation) are causal, meaning they require knowledge of the data-generating process and cannot be answered by joint distributions alone.
- **The Educational Gap**: Traditional statistics lacks the mathematical language to express causal assumptions, leading to a disconnect between data and causal conclusions.
- **The Structural Theory**: Pearl proposes the Structural Causal Model (SCM) as a unifying framework that subsumes graphical models, potential outcomes, and structural equations.,

### 2. From association to causation

- **2.1 The basic distinction: Coping with change**
    - Statistical analysis deals with static conditions (observing). Causal analysis deals with changing conditions (intervening).
    - **Invariance Principle | 不变性原则**: Causal assumptions identify relationships that remain invariant when external conditions change.
- **2.2 Formulating the basic distinction**
    - Associational Concept | 关联性概念: Defined by joint distributions (e.g., Correlation, Regression).
    - Causal Concept | 因果性概念: Cannot be defined by distributions alone (e.g., Confounding, Randomization, Counterfactuals).
- **2.3 Ramifications of the basic distinction**
    - **The Golden Rule**: Behind every causal conclusion there must lie some causal assumption that is untestable in observational studies.,
    - Confounding | 混淆 cannot be defined by association alone; attempting to do so leads to biased adjustments (e.g., adjusting for a mediator).
- **2.4 Two mental barriers: Untested assumptions and new notation**
    - Barrier 1: Acceptance of judgmental, untested assumptions as part of the formal model.
    - Barrier 2: Necessity of new notation like $P(Y=y|do(X=x))$ or $Y_x(u)$ because standard probability calculus ($P(y|x)$) cannot distinguish "seeing" from "doing".,

### 3. Structural models, diagrams, causal effects, and counterfactuals

- **3.1 Introduction to structural equation models (SEM)**
    - Causal directionality is represented by $y = f(x, u)$ where nature assigns $y$ based on $x$, but $x$ is not necessarily assigned based on $y$.
    - **Exogenous Variables | 外生变量 ($U$)**: Factors outside the model (disturbances/errors) that represent physical reality (e.g., genetics).
    - **Endogenous Variables | 内生变量 ($V$)**: Variables determined by other variables within the model.
    - Causal assumptions are encoded in the **missing links** of a diagram.
    - **d-separation | d-分离**: A graphical criterion that links the model structure to conditional independence in the data.
- **3.2 From linear to nonparametric models and graphs**
    - **3.2.1 Representing interventions**
        - **do-operator | do算子**: Simulates an intervention by deleting the equation for $X$ and replacing it with a constant $x$, creating a "mutilated" model $M_x$.
        - Post-intervention Distribution: $P(y|do(x))$ represents the population response to a uniform treatment.
    - **3.2.3 Causal effects from data and graphs**
        - **Causal Markov Condition**: Any distribution from a Markovian model factorizes as $P(v_1, \dots, v_n) = \prod P(v_i | pa_i)$.
        - **Truncated Factorization | 截断因式分解**: $P(v \setminus x | do(x)) = \prod_{i|V_i \notin X} P(v_i | pa_i)$. This allows predicting interventional results from observational data.
- **3.3 Coping with unmeasured confounders**
    - **3.3.1 Covariate selection – the back-door criterion**
        - A set $S$ is sufficient for adjustment if:
            - (1) it contains no descendants of $X$, and
            - (2) it blocks all "back-door" paths from $X$ to $Y$ (paths ending with an arrow into $X$).
        - Adjustment Formula: $P(y|do(x)) = \sum_s P(y|x, s) P(s)$.
    - **3.3.2 General control of confounding**
        - When back-door adjustment fails, multi-stage adjustments (e.g., Front-door criterion) or **do-calculus** can be used.,
- **3.4 Counterfactual analysis in structural models**
    - Unit-level Counterfactual | 个体级逆事实: $Y_x(u)$ is defined as the solution for $Y$ in the modified model $M_x$ for a specific unit $u$.
    - This bridges the gap between population-level "causal effects" and unit-level "attribution" (e.g., "Socrates died because he drank hemlock").
- **3.5 An example: Non-compliance in clinical trials**
    - Uses Instrumental Variables | 工具变量 ($Z$) to bound causal effects when compliance is imperfect.,
    - **Instrumental Inequality**: A testable implication $\max_x \sum_y [\max_z P(x, y|z)] \leq 1$ that can refute the validity of an instrument.

### 4. The potential outcome framework

- **4.1 The “Black-Box” missing-data paradigm**
    - Potential outcomes ($Y_x$) are treated as missing data. The observed $Y$ is connected via the consistency constraint: $X=x \Rightarrow Y_x = Y$.,
- **4.2 Problem formulation and the demystification of “ignorability”**
    - "Ignorability" ($Y_x \perp X | Z$) is often hard to justify without graphs. SCM provides a process-based foundation for these independence assumptions.,
- **4.3 Combining graphs and potential outcomes**
    - Rules for translation: Missing arrows imply exclusion restrictions ($Y_{pa_Y} = Y_{pa_Y, s}$); missing dashed arcs imply independence restrictions ($Y_{pa_Y} \perp Z_{pa_Z}$).,

### 5. Counterfactuals at work

- **5.1 Mediation: Direct and indirect effects**
    - **Controlled Direct Effect (CDE)**: Fixed by intervention on the mediator $Z$.
    - **Natural Direct Effect (NDE)**: The effect of $X$ while $Z$ is kept at the value it _would have taken_ under the baseline $X=x$.
    - **Mediation Formula | 中介公式**: $IE_{x, x'} = \sum_z E(Y|x, z)[P(z|x') - P(z|x)]$.
- **5.2 Causes of effects and probabilities of causation**
    - **Probability of Necessity (PN) | 必要性概率**: $P(Y_{x'} = y' | X=x, Y=y)$. Measures attribution (e.g., legal responsibility).
    - Identifiable under the assumption of **Monotonicity | 单调性**.

---

### 3. Summary and Evaluation

### (1) Research Problem

- **Motivation**: To solve the "linguistic handicap" of statistics, allowing researchers to formally analyze causal questions that traditional probability cannot handle.,
- **Claimed Contribution**: A comprehensive Structural Causal Model (SCM) that unifies graphical models, SEM, and potential outcomes, providing algorithmic solutions for identification, mediation, and attribution.,
- **Implicit Assumption**: The existence of a stable, modular data-generating process (Nature) that can be represented as a set of autonomous functional mechanisms.,

### (2) Core Idea

- Causality is not about data distributions but about the **invariants** of the data-generating process under external change. These invariants are captured by SCMs and the $do(x)$ operator.,

### (3) Experiments

- **What is actually tested?** The paper provides mathematical proofs and logic-based derivations illustrated by clinical trial non-compliance and employment discrimination scenarios.,
- **Does experiment logically support the claim?** Yes; the derivation of instrumental inequalities and the mediation formula provides testable boundaries and estimands for previously "unsolvable" problems.,

### (4) Limitations

- **Stated Limitations**: Causal conclusions are strictly conditional on the correctness of the qualitative causal assumptions (the graph).,
- **Unstated Weakness**: The framework relies heavily on DAGs (Directed Acyclic Graphs); cyclic models (feedback loops) are mentioned but not fully developed in this specific overview.
- **Boundary Conditions**: Non-parametric identification requires specific graph topologies; if a "bow-pattern" exists between a variable and its effect, identifying the effect without further assumptions is impossible. [E13 analysis/context]

---

### Constructive Questions

1. **Model Robustness**: Given that identification is sensitive to the graph structure, how can we develop automated "sensitivity analysis" tools to quantify how much a causal estimate would change if a single arrow was added or removed?
2. **Beyond Acyclicity**: How do the rules of $do-calculus$ and the back-door criterion change in high-frequency time-series data where feedback loops ($X \rightarrow Y \rightarrow X$) are the norm rather than the exception?
3. **Data-Model Conflict**: If the "Instrumental Inequality" is violated in a real-world dataset, what is the systematic procedure for "repairing" the causal diagram rather than just rejecting the instrument?