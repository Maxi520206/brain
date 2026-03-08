### [E4] Schölkopf, B., Locatello, F., Bauer, S., Ke, N. R., Kalchbrenner, N., Goyal, A., & Bengio, Y. (2021). Toward Causal Representation Learning. _Proceedings of the IEEE_, 109(5), 612–634.

---

#### 1. Preliminaries

- **Keywords**: Causal Representation Learning | 因果表示学习, Independent Causal Mechanisms (ICM) | 独立因果机制, Out-of-distribution (OOD) Generalization | 分布外泛化, Structural Causal Models (SCM) | 结构因果模型, Disentanglement | 解耦.
- **Reference**:
    - **Pearl, J. (2009). _Causality: Models, Reasoning, and Inference_.**
        - Provides the formal language (SCMs, do-calculus) for modeling interventions and counterfactuals used as the paper's foundation.
    - **Peters, J., Janzing, D., & Schölkopf, B. (2017). _Elements of Causal Inference_.**
        - Connects algorithmic information theory with causal discovery and establishes the principles of ICM.
    - **Vapnik, V. N. (1998). _Statistical Learning Theory_.**
        - Defined the IID-based framework that current ML relies on, which this paper seeks to extend.

---

#### 2. Lecture Note: Toward Causal Representation Learning

##### I. INTRODUCTION

- **The Gap**: ML excels at pattern recognition on IID data | 独立同分布数据 but fails at "Strong Generalization" | 强泛化 (transferring to new problems/distributions) where animals excel.
- **Issue 1—Robustness**: Current deep learning is vulnerable to distribution shifts (camera blur, noise) and adversarial attacks. Fixes like data augmentation are insufficient; a causal model is required to understand underlying mechanisms.
- **Issue 2—Learning Reusable Mechanisms**: Natural intelligence reuses physical understanding across tasks. Modular representations matching physical causal mechanisms allow for efficient adaptation with fewer examples.
- **Causality Perspective**: Causation requires the notion of Intervention | 干预. It acquired robust knowledge that holds beyond the observed distribution.
- **Objective**: To move toward AI that involves "thinking" (acting in an imagined space) by modeling the effect of interventions and distribution changes.

##### II. LEVELS OF CAUSAL MODELING

- **Mechanistic/Physical**: Gold standard; uses differential equations ($dx/dt = f(x)$) to explain functioning and read off causal structure.
- **Statistical Models**: Superficial; only models associations. Accuracy holds only if experimental conditions remain fixed (e.g., storks vs. birth rates).
- **Causal Models**: Lie in between; use data-driven learning with weak assumptions (SCMs) to predict the effect of interventions and counterfactuals.

##### III. CAUSAL MODELS AND INFERENCE

- **A. Methods Driven by i.i.d. Data**: Current successes rely on massive data and high-capacity systems but perform poorly when IID is violated (e.g., placing objects in unfamiliar contexts).
- **B. Reichenbach Principle**: If $X$ and $Y$ are dependent, there is a common cause $Z$. Observational data alone cannot distinguish $X \to Y$ from $X \leftarrow Y$ without assumptions.
- **C. Structural Causal Models (SCMs)**:
    - Variables $X_i$ are assigned via $X_i := f_i(PA_i, U_i)$, where $PA_i$ are parents and $U_i$ is independent noise.
    - **Causal Factorization | 因果分解**: $P(X_1, \dots, X_n) = \prod P(X_i | PA_i)$. This decomposes the joint distribution into autonomous Causal Mechanisms | 因果机制.
- **D. Differences**: Statistical models represent one distribution; causal models represent a set of distributions (one for each intervention) [39, Fig 1]. SCMs are the only level allowing Counterfactuals | 逆事实 by fixing noise variables $U_i$.

##### IV. INDEPENDENT CAUSAL MECHANISMS (ICM)

- **ICM Principle**: The generative process consists of autonomous modules that do not inform or influence each other.
    - Intervention on one mechanism does not change others.
    - Knowing one mechanism gives no info about another.
- **Sparse Mechanism Shift (SMS) Hypothesis | 稀疏机制偏移假设**: Small distribution changes manifest locally/sparsely in the causal factorization, whereas they appear "entangled" in non-causal factorizations.
- **Algorithmic Independence**: Mechanisms are independent if their shortest joint description (Kolmogorov complexity) is the sum of individual descriptions.

##### V. CAUSAL DISCOVERY AND MACHINE LEARNING

- **Constraint-based Discovery**: Uses conditional independence tests but is difficult for high-dimensional/continuous data.
- **Functional Assumptions**: In the bivariate case ($X, Y$), additive noise models ($Y = f(X) + V$) can break the symmetry to identify the causal direction.
- **Exploiting Shifts**: Distribution shifts (contexts) help identify structure; causal models adapt faster to sparse interventions than predictive ones.

##### VI. LEARNING CAUSAL VARIABLES

- **The Core Problem**: Most causality work assumes variables are given. **Causal Representation Learning | 因果表示学习** strives to discover high-level causal units ($S$) from low-level raw data ($X = G(S)$).
- **Integration**: Embedding an SCM into a modular neural network architecture. The SMS hypothesis serves as a bias: interventions should only affect a few causal variables (e.g., moving a finger) even if many pixels change [65-66, Fig 3].

##### VII. IMPLICATIONS FOR MACHINE LEARNING

- **A. Semi-supervised Learning (SSL)**:
    - In **Causal direction** ($X \to Y$): SSL should be futile because $P(X)$ contains no info about $P(Y|X)$ (ICM principle).
    - In **Anticausal direction** ($Y \to X$): SSL is feasible because $P(X)$ contains info about $P(Y|X)$.
- **B. Adversarial Vulnerability**: Anticausal classifiers (predicting cause from effect) are more vulnerable. Defenses include "Analysis by Synthesis" (modeling the causal generative direction).
- **C. Robustness**: Causal features are stable against "strategic behavior" (e.g., changing address vs. paying debt for credit scores).
- **E. Reinforcement Learning**: RL is essentially causal induction (learning relations) and inference (planning). Counterfactuals can improve data efficiency and help agents reflect on past actions.
- **F. Scientific Applications**: Causal models have helped detect exoplanets (Kepler mission) by removing instrument confounding.

---

#### 3. Summary and Evaluation

##### (1) Research Problem

- **Motivation**: Traditional ML is limited to pattern recognition on fixed distributions and lacks the ability to reason about changes, interventions, or counterfactuals.
- **Claimed Contribution**: Reviews and synthesizes the intersection of causality and ML; proposes "Causal Representation Learning" as the next frontier for AI.
- **Implicit Assumption**: The world consists of independent, autonomous physical mechanisms that can be represented as modular components in a learning system.

##### (2) Core Idea

- ML should move from learning statistical associations ($P(Y|X)$) to learning structural representations ($SCMs$) that are invariant across tasks and robust to interventions.

##### (3) Experiments

- **What is actually tested?** The paper is a survey/perspective article. It cites specific empirical results like SSL performance on causal/anticausal tasks and exoplanet discovery.
- **Does experiment support the claim?** Yes, the cited evidence in astronomy and SSL benchmarks demonstrates that considering causal direction improves robustness and discovery.

##### (4) Limitations

- **Stated Limitations**: Scaling non-linear causal discovery to large numbers of variables remains difficult; algorithms for unstructured raw data are in early stages.
- **Unstated Weakness**: The SMS hypothesis is an inductive bias; if the world is highly interconnected with many dense shifts, the "sparse" assumption may fail.
- **Boundary Conditions**: The framework largely assumes acyclic models (DAGs), which may not apply to systems with continuous feedback loops.

---

#### 4. Constructive Questions

1. **Granularity Discovery**: How can a model automatically determine the "right" level of abstraction (granularity) for causal variables depending on the specific downstream task?
2. **Entanglement in Optimization**: If we use a single end-to-end neural network, how can we prevent the parameters of different "independent mechanisms" from becoming entangled during the gradient descent process?
3. **Data Requirements**: Is it possible to perform causal representation learning purely from observational data without any environment labels or interventions, given the identifiability challenges mentioned?