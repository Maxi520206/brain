---
tags:
  - Machine_Learning
  - Causal_Inference
year: 2017
Authur: Bernhard Schölkopf
---
- **Keywords**: Causal Inference | 因果推断, Machine Learning | 机器学习, Robustness | 鲁棒性, Structural Causal Models | 结构因果模型, Independent Causal Mechanisms | 独立因果机制.
- **Reference**:
    - **Pearl, J. (2009a). _Causality: Models, Reasoning, and Inference_.**
        - Established the mathematical foundation for structural causal models and the logic of interventions.
    - **Vapnik, V. N. (1998). _Statistical Learning Theory_.**
        - Defined the framework for supervised learning based on the IID assumption.
    - **Peters, J., Janzing, D., & Schölkopf, B. (2017). _Elements of Causal Inference_.**
        - Provides the foundational principles connecting causal discovery with statistical properties.

---

### 1. Introduction

- **Gap between ML and Natural Intelligence**:
    - Current ML excels at pattern recognition but fails at transfer to new problems and out-of-distribution generalization.
    - Animals utilize information that ML often treats as "nuisance": interventions, domain shifts, and temporal structure.
- **Goal**: Using causality to model and reason about interventions to enable "thinking" in the sense of acting in an imagined space.

### 2. The Mechanization of Information Processing

- **Historical Parallel**: Information | 信息 is to the digital revolution what Energy | 能量 was to the industrial revolution.
- **Industrialization of AI**: Transition from human-programmed rules to automated learning from data.
- **Future Markets**: Anticipating a shift from statistical dependence markets to markets for directed/interventional information.

### 3. From Statistical to Causal Models

- **Limitations of IID Data**:
    - IID Assumption | 独立同分布假设: Data points are independent and identically distributed.
    - Successes in big data rely on IID, but performance collapses under targeted violations (e.g., adversarial attacks, contextual shifts).
- **Common Cause Principle | 共因原则**:
    - If $X$ and $Y$ are dependent, there exists a variable $Z$ influencing both.
    - Observational data alone cannot distinguish between $X \rightarrow Y$, $X \leftarrow Y$, and $X \leftarrow Z \rightarrow Y$ without further assumptions.
- **Structural Causal Models (SCMs) | 结构因果模型**:
    - Each observable $X_i$ is an assignment: $X_i := f_i(PA_i, U_i)$, where $PA_i$ are parents and $U_i$ is independent noise.
    - **Causal Markov Condition | 因果马尔可夫条件**: Conditioned on parents, a variable is independent of its non-descendants.
    - **Causal Factorization | 因果分解**: The joint distribution decomposes into causal mechanisms: $p(X_1, \dots, X_n) = \prod p(X_i | PA_i)$.

### 4. Levels of Causal Modelling

- **Taxonomy of Models**:
    1. **Mechanistic/Physical**: Differential equations; predicts everything (IID, shifts, counterfactuals).
    2. **Structural Causal**: SCMs; predicts shifts and answers counterfactuals.
    3. **Causal Graphical**: DAGs; predicts shifts but usually not counterfactuals.
    4. **Statistical**: Predictive in IID settings only; no insight into interventions.
- **Physics Connection**: A solved differential equation $\frac{dx}{dt} = f(x)$ allows one to read off the causal structure directly.

### 5. Independent Causal Mechanisms (ICM)

- **ICM Principle | 独立因果机制原则**: The causal generative process consists of autonomous modules that do not inform or influence each other.
- **Implications**:
    - Intervening on one mechanism $p(X_i | PA_i)$ does not change others.
    - Knowledge of one mechanism provides no information about another.
- **Algorithmic Independence**: Defined via Kolmogorov complexity | 柯氏复杂度; mechanisms are independent if their shortest joint description is the sum of individual descriptions.
- **Thermodynamics Connection**: ICM implies the second law of thermodynamics (entropy/complexity non-decreasing over time).

### 6. Cause-Effect Discovery

- **Bivariate Case**: Since conditional independence testing requires $\ge 3$ variables, the two-variable case requires functional assumptions.
- **Additive Noise Model (ANM) | 加性噪声模型**: $Y = f(X) + V$.
    - Under generic conditions, an ANM can fit in the causal direction but not the anticausal direction.
- **Role of Machine Learning**: ML helps by providing kernels and function class complexity measures to detect causal directions.

### 7. Half-Sibling Regression and Exoplanet Detection

- **Problem**: Instrument noise acts as a Confounder | 混淆变量 for stars light-years apart.
- **Half-Sibling Regression | 半同胞回归**: Predict a star's noise using other stars (siblings sharing the same instrument) to cancel the confounder.
- **Result**: Enabled validation of 21 exoplanets, including K2-18b in the habitable zone.

### 8. Invariance, Robustness, and Semi-Supervised Learning

- **Invariance Principle**: Causal mechanisms should be invariant across different domains/environments.
- **Semi-Supervised Learning (SSL) | 半监督学习**:
    - **Prediction**: SSL is futile for Causal Learning | 因果学习 ($X \rightarrow Y$) because $p(X)$ contains no info about $p(Y|X)$.
    - **Prediction**: SSL is feasible for **Anticausal Learning | 逆因果学习** ($Y \rightarrow X$) because $p(X)$ (the effect) contains info about $p(Y|X)$.
- **Adversarial Vulnerability**: Anticausal classifiers are more vulnerable because they model a non-robust $p(y|x)$. Causal models (analysis by synthesis) offer a defense.

### 9. Causal Representation Learning

- **The Challenge**: Real-world data is unstructured (e.g., pixels). We must learn the causal variables $S_i$ from raw data $X$.
- **Causal Representation Learning | 因果表示学习**: Embedding an SCM into a generative model (e.g., VAE or GAN) to extract high-level causal units.
- **Disentangled Representations | 解耦表示**: Identifying independent factors of variation. Causal version requires these factors to be independently intervenable.
- **Significance**: Moves ML from representing statistical dependence to supporting planning, reasoning, and "imagined" intervention.

---

# Summary and Evaluation

### (1) Research Problem

- **Motivation**: Standard ML is limited to IID pattern recognition and lacks the robustness/generalization required for human-level AI.
- **Claimed Contribution**: Synthesizing the links between graphical causal inference and ML, proposing the ICM principle as a bridge to solve open ML problems.
- **Implicit Assumption**: The world is modular and physical laws (mechanisms) are independent in an informational sense.

### (2) Core Idea

- Use the **Independent Causal Mechanisms (ICM)** principle and **Structural Causal Models (SCM)** to build modular, invariant representations that generalize beyond the training distribution.

### (3) Experiments

- **What is actually tested?**
    - The paper primarily serves as a theoretical overview and synthesis.
    - Specific evidence cited includes the "Half-sibling regression" for exoplanet data and a meta-analysis of SSL studies supporting the causal/anticausal learning hypothesis.
- **Does experiment support the claim?** Yes, the astronomical results provide a high-impact real-world validation of causal confounding removal.

### (4) Limitations

- **Stated Limitations**: Identification analysis often assumes infinite sample sizes and ignores sampling variability.
- **Unstated Weakness**: The "Causal Representation Learning" task remains largely conceptual; discovering causal units from raw pixels without any supervision is still an extremely difficult, potentially ill-posed problem.
- **Boundary Conditions**: The ICM principle might be violated in systems with high feedback or where variables are defined in a way that "crosses" causal boundaries.

---

<aside> 💡

### Constructive Questions

1. How can we define "minimal" causal variables in representation learning such that they are not just statistically independent but also semantically meaningful for a specific set of tasks?
2. In the absence of interventional data, what specific inductive biases (beyond the Additive Noise Model) are most promising for identifying causal direction in high-dimensional, non-linear ML settings?
3. How does the "Algorithmic Independence" of mechanisms scale to deep learning architectures where parameters are highly entangled by the optimization process (e.g., SGD)? </aside>