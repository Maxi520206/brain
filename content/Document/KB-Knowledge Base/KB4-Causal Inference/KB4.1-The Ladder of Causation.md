# [[B32C1-The Ladder of Causation]]

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

2026/03/02

> [[B32C1]The Ladder of Causation](https://www.notion.so/B32C1-The-Ladder-of-Causation-317bcf323f7c80a48c72d61c6650fbf5?pvs=21)

---