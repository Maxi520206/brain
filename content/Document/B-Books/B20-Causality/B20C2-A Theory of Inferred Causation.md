
### 2.1 Introduction – The Basic Intuitions

- **Inductive Acquisition | 归纳获取**: Intelligent systems must translate passive observations into cause-and-effect relationships.
- **Temporal Precedence | 时间优先性**: While a vital clue, time order alone cannot distinguish genuine causation from spurious associations (e.g., the barometer falling before rain).
- **Directionality Clues**: Certain statistical dependency patterns, such as the intransitive pattern $A \to B \leftarrow C$ (where $A, C$ are independent but both affect $B$), reveal causal direction even without temporal information.

---

### 2.2 The Causal Discovery Framework

- **Induction Game**: Causal discovery is viewed as a game scientists play against Nature, which possesses stable, deterministic functional mechanisms.
- **Definition 2.2.1 Causal Structure | 因果结构**: A directed acyclic graph (DAG) where nodes are variables and links represent direct functional relationships.
- **Definition 2.2.2 Causal Model | 因果模型**: A pair $M = \langle D, \Theta \rangle$ where $D$ is a causal structure and $\Theta$ assigns:
    - A function $x_i = f_i(pa_i, u_i)$ for each variable.
    - A probability measure $P(u_i)$ for random disturbances $U_i$, which are mutually independent.
- **Markov Condition | 马尔可夫条件**: Independent disturbances render each variable independent of all its nondescendants, conditional on its parents.

---

### 2.3 Model Preference (Occam's Razor)

- **Model Underspecification**: Without constraints, an unbounded number of latent variable models can fit any observed distribution.
- **Minimal Model | 最小模型**: A theory is ruled out if there exists a simpler, less elaborate theory equally consistent with the data.
- **Definition 2.3.1 Inferred Causation (Preliminary)**: Variable $X$ has causal influence on $Y$ if a directed path from $X$ to $Y$ exists in every minimal structure consistent with the data.
- **Definition 2.3.6 Inferred Causation (General)**: $C$ has causal influence on $E$ if a directed path exists in every minimal latent structure consistent with the observed distribution.

---

### 2.6 Recovering Latent Structures

- **Projection | 投影**: A way to represent latent structures using bidirectional graphs containing only observed variables.
- **Bidirected Links | 双向链接**: Represent common hidden causes between variables.

---

### 2.7 Local Criteria for Inferring Causal Relations

The labels produced by discovery algorithms (like IC*) serve as formal definitions for types of causation.

### 2.7.1 Potential Cause | 潜在原因

- $X$ is a potential cause of $Y$ if:
    1. $X$ and $Y$ are dependent in every context.
    2. There exists a variable $Z$ and a context $S$ such that $(X \perp Z | S)$ and $(Z \not\perp Y | S)$.

### 2.7.2 Genuine Cause | 真实原因

- $X$ has a genuine causal influence on $Y$ if there is a variable $Z$ such that:
    1. $Z$ is a potential cause of $X$.
    2. $Z$ and $Y$ are dependent given some context $S$.
    3. $Z$ and $Y$ are independent given $S \cup {X}$.
- **Intuition**: If conditioning on $X$ destroys the dependence between a potential cause of $X$ and the variable $Y$, the mediation must be causal.

### 2.7.4 Genuine Causation with Temporal Information

- If $X$ precedes $Y$ in time, $X$ influences $Y$ if there exists $Z$ and $S$ (both occurring before $X$) such that:
    1. $(Z \not\perp Y | S)$.
    2. $(Z \perp Y | S \cup {X})$.

---

### 2.8 Nontemporal Causation and Statistical Time

- **Expectations of Explanation**: Causal explanations must satisfy temporal (cause precedes effect) and statistical (causes screen off their effects) expectations.
- **Statistical Time | 统计时间**: The directionality determined solely by statistical dependencies.
- **Temporal Bias**: In nature, physical time usually coincides with statistical time; current states often render future variables independent, but rarely past variables.

---

### 2.9 Conclusions

- **Autonomy | 自主性**: Mechanisms are invariant and can vary independently of one another.
- **Stability (Faithfulness) | 稳定性/忠实性**: The assumption that the observed patterns of dependency are inherent to the structure and not the result of coincidental parameter values.
- **Common Cause Principle**: Correlations that are not explained by direct causation are attributed to common causes.