[[E13-Causal Diagrams for Empirical Research]]
[[KB4.2-Causal Model]]

### 3.1 Introduction

- **Objective**: To infer causal relationships from a combination of data and qualitative causal assumptions.
- **Central Task**: Deciding whether provided assumptions are sufficient to assess the strength of causal effects from nonexperimental (observational) data.
- **Core Utility**: Causal effects allow the prediction of how systems respond to hypothetical interventions (e.g., policy decisions).

### 3.2 Intervention in Markovian Models

#### 3.2.1 Graphs as Models of Interventions

- **Mechanism-based Account | 基于机制的解释**: Causal assertions represent autonomous physical mechanisms; each child–parent family in a DAG $G$ represents a deterministic function $x_i = f_i(pa_i, \epsilon_i)$.
- **Independent Disturbances**: $\epsilon_i$ are jointly independent random disturbances representing background factors omitted from the model.
- **Semi-Markovian Models**: Models where some background variables are dependent (represented by bidirected arcs), while the graph remains acyclic.
- **Intervention | 干预**: An alteration of a subset of mechanisms while others remain intact.
- **Causal Effect | 因果效应**: Denoted as $P(y | \hat{x})$ or $P(y | do(x))$, it is the probability of $Y=y$ induced by deleting equations for $X$ and substituting $X=x$ in the remaining equations.

#### 3.2.2 Interventions as Variables

- **Augmented Network | 增强网络 ($G'$)**: Treating the force of intervention as a variable $F_i$ added to the parent set of $X_i$.
- **Locality**: Only descendants of $X_i$ are affected by changes in the mechanism governing $X_i$.

#### 3.2.3 Computing the Effect of Interventions

- **Truncated Factorization | 截断因子分解**: For an atomic intervention $do(x'_i)$: $$P(x_1, \dots, x_n | \hat{x}'_i) = \begin{cases} \prod_{j \neq i} P(x_j | pa_j) & \text{if } x_i = x'_i \ 0 & \text{if } x_i \neq x'_i \end{cases}$$.
- **Mass Transfer**: In $P(y | \hat{x}'_i)$, mass from points where $X_i \neq x'_i$ is transferred to points sharing the same $pa_i$.
- **Adjustment for Direct Causes | 直接原因调整**: $$P(y | \hat{x}'_i) = \sum_{pa_i} P(y | x'_i, pa_i) P(pa_i)$$.

#### 3.2.4 Identification of Causal Quantities

- **Identifiability | 可识别性**: A quantity $Q$ is identifiable if it can be computed uniquely from the observed distribution $P(v)$ given the causal graph $G$.
- **Requirement**: Requires $P(v) > 0$ and consistent qualitative features in $G$ across models.

### 3.3 Controlling Confounding Bias

- **Covariates | 协变量**: Factors used for adjustment (standardization) to remove bias.
- **Simpson's Paradox**: The phenomenon where statistical relationships reverse when additional factors are included.

#### 3.3.1 The Back-Door Criterion

- **Definition**: A set $Z$ satisfies the back-door criterion relative to $(X, Y)$ if:
    1. No node in $Z$ is a descendant of $X$.
    2. $Z$ blocks every path between $X$ and $Y$ that contains an arrow into $X$ (back-door paths).
- **Back-Door Adjustment | Back-door 调整**: $$P(y | \hat{x}) = \sum_z P(y | x, z) P(z)$$.

#### 3.3.2 The Front-Door Criterion

- **Definition**: A set $Z$ satisfies the front-door criterion relative to $(X, Y)$ if:
    1. $Z$ intercepts all directed paths from $X$ to $Y$.
    2. There is no unblocked back-door path from $X$ to $Z$.
    3. All back-door paths from $Z$ to $Y$ are blocked by $X$.
- **Front-Door Adjustment | Front-door 调整**: $$P(y | \hat{x}) = \sum_z P(z | x) \sum_{x'} P(y | x', z) P(x')$$.

#### 3.3.3 Example: Smoking and the Genotype Theory

- Uses Tar ($Z$) as a mediator between Smoking ($X$) and Cancer ($Y$) to demonstrate the identification of effects when Smoking and Cancer are confounded by a hidden genotype ($U$).

### 3.4 A Calculus of Intervention

- **do Calculus | $do$ 演算**: Inference rules for transforming expressions involving interventions and observations.

#### 3.4.1 Preliminary Notation

- $G_{\overline{X}}$: Arrows pointing to $X$ deleted.
- $G_{\underline{X}}$: Arrows emerging from $X$ deleted.

#### 3.4.2 Inference Rules

- **Rule 1 (Observation insertion/deletion)**: $P(y | \hat{x}, z, w) = P(y | \hat{x}, w)$ if $(Y \perp Z | X, W)_{G_{\overline{X}}}$.
- **Rule 2 (Action/observation exchange)**: $P(y | \hat{x}, \hat{z}, w) = P(y | \hat{x}, z, w)$ if $(Y \perp Z | X, W)_{G_{\overline{X}\underline{Z}}}$.
- **Rule 3 (Action insertion/deletion)**: $P(y | \hat{x}, \hat{z}, w) = P(y | \hat{x}, w)$ if $(Y \perp Z | X, W)_{G_{\overline{X}, \overline{Z(W)}}}$.
- **Completeness**: These rules are sufficient for deriving all identifiable causal effects.

#### 3.4.3 Symbolic Derivation of Causal Effects: An Example

- Demonstrates reducing the front-door estimand to a $do$-free expression using Rules 1-3.

#### 3.4.4 Causal Inference by Surrogate Experiments

- **Surrogate Variable | 代理变量 ($Z$)**: A controllable variable used to identify $P(y | \hat{x})$ when direct control of $X$ is infeasible.

### 3.5 Graphical Tests of Identifiability

#### 3.5.1 Identifying Models

- **Bow Pattern | 弓形模式**: A confounding arc embracing a causal link $X \to Y$; its presence prevents identification of $P(y | \hat{x})$.
- **Mediating Variables**: The introduction of observed mediating variables can assist, but never impede, identifiability.

#### 3.5.2 Nonidentifying Models

- **Necessary Condition for Nonidentifiability**: The presence of an unblockable back-door path between $X$ and $Y$.

### 3.6 Discussion

#### 3.6.1 Qualifications and Extensions

- Causal assumptions primarily serve as a precise language for deliberation rather than being directly testable by statistical data.

#### 3.6.2 Diagrams as a Mathematical Language

- The "hat" notation ($\hat{x}$) clarifies the empirical basis of structural equations by distinguishing "holding fixed" from "conditioning".

#### 3.6.3 Translation from Graphs to Potential Outcomes

- **Potential Outcome | 潜在结果 ($Y_x(u)$)**: The value $Y$ would obtain in unit $u$ had $X$ been $x$.
- **Structural Interpretation**: $Y_x(u)$ is the unique solution of $Y$ in the submodel $M_x$.

#### 3.6.4 Relations to Robins’s G-Estimation

- **G-computation Formula**: A recursive formula for identifying the effect of time-varying treatments, derived from sequential ignorability.