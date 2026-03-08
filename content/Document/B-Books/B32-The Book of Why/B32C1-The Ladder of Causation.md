### 1.1 The Ladder of Causation | 因果之梯

- **Definition**: A central metaphor used to classify cognitive systems based on the power of the causal queries they can answer.
- **Fundamental Premise**: No machine can derive causal explanations from raw data alone; it requires a mental model of reality.
- **Modularity | 模块化**: Causal models are modular, meaning local alterations (e.g., changing one variable) can be made without re-evaluating the entire system.

---

### 1.2 The Three Levels of Causation

The ladder consists of three tiers, each progressively more powerful than the one below.

### 1.2.1 Rung 1: Association | 关联 (Seeing)

- **Activity**: Observing regularities in data to identify associations between variables.
- **Core Query**: "What if I see...?" (How does seeing $X$ change my belief in $Y$?).
- **Characteristics**:
    - Calls for predictions based on passive observations.
    - Uses conditional probability | 条件概率, denoted as $P(Y|X)$.
    - Cannot determine directionality (e.g., whether toothpaste causes flossing or vice versa).
    - **Machine Learning Status**: Most present-day deep learning systems share the "wisdom of an owl" and reside at this level.

### 1.2.2 Rung 2: Intervention | 干预 (Doing)

- **Activity**: Actively changing the world to see the result.
- **Core Query**: "What if I do...?" or "How can I make $Y$ happen?".
- **Mathematical Form**: The $do$-operator | $do$ 算子, denoted as $P(Y|do(X))$.
- **Characteristics**:
    - Involves breaking the rules of the natural environment to enforce a specific value.
    - Distinguishes between "seeing" smoke and "making" smoke.
    - Requires a causal model to predict effects without actually performing the experiment.

### 1.2.3 Rung 3: Counterfactuals | 反事实 (Imagining)

- **Activity**: Retrospection and imagining worlds that contradict observed reality.
- **Core Query**: "What if I had done...?" or "Why?".
- **Characteristics**:
    - Compares the observed world with a fictitious, contradictory world.
    - **Algorithmization of Counterfactuals | 反事实算法化**: Emulating human retrospective thinking through a formal model.
    - Requires a "theory" or "law of nature" to bridge the gap between what is seen and what is unseen.

---

### 1.3 The Mini-Turing Test | 迷你图灵测试

- **Goal**: To encode a simple story in a machine so that it can answer causal questions correctly as a human child would.
- **Core Tool**: Causal Diagram | 因果图. It provides a compact representation for extracting answers.

### 1.3.1 Case Study: The Firing Squad | 处决队

- **Variables**: Court Order ($CO$), Captain's signal ($C$), Soldier $A$ ($A$), Soldier $B$ ($B$), and Prisoner's Death ($D$).
- **Level 1 (Association)**: If the prisoner is dead, we conclude $A$ shot, $B$ shot, and $CO$ was given.
- **Level 2 (Intervention)**: If Soldier $A$ decides to fire independently ($do(A=true)$):
    - **Surgery | 手术**: Erase arrows pointing to $A$ (emancipate it from the Captain).
    - **Result**: $D$ is true, but we conclude $B$ did not shoot.
- **Level 3 (Counterfactual)**: If the prisoner is dead, what if $A$ had not fired?
    - **Analysis**: We know $C$ signaled and $B$ shot.
    - **Result**: The prisoner would still be dead in the fictitious world because of $B$'s shot.

---

### 1.4 Probabilities and Causation

- **Probability Raising | 概率提升**: The intuitive idea that a cause $X$ makes effect $Y$ more likely.
- **The Confounding Impasse**: Confusing $P(Y|X) > P(Y)$ (Association) with $P(Y|do(X)) > P(Y)$ (Intervention) led to decades of failed attempts to define causation.
- **The Role of Confounders**: High ice-cream sales are associated with high crime due to a common cause (heat), but wiggling ice-cream sales does not affect crime.
- **Robustness**: Causal structures (diagrams) remain invariant even when the underlying probabilities change (e.g., introduction of a safer vaccine).