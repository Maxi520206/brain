
### 2.1 The importance of thinking conditionally

- **Core Concept**: Conditional probability allows for incorporating evidence into our understanding of the world by updating probabilities as new information arrives.
- **Perspective**: All probabilities are technically conditional, as they rely on a set of background assumptions or knowledge $K$.
- **Key Phrase**: "Conditioning is the soul of statistics."

### 2.2 Definition and intuition

**Definition 2.2.1 | 条件概率**:

- If $A$ and $B$ are events with $P(B) > 0$, the conditional probability of $A$ given $B$ is: $[ P(A|B) = \frac{P(A \cap B)}{P(B)} ]$
- **Prior Probability | 先验概率 ($P(A)$)**: The assessment of probability before updating based on evidence $B$.
- **Posterior Probability | 后验概率 ($P(A|B)$)**: The updated probability after observing evidence $B$.
- **Note**: $P(A|B)$ is the probability of event $A$ given evidence $B$; there is no such event as "$A|B$".
- **Intuitions**:
    - **Pebble World**: Eliminate all pebbles (outcomes) in $B^c$, then renormalize the masses of the remaining pebbles in $B$ so they sum to 1.
    - **Frequentist Interpretation**: The fraction of times $A$ occurs in trials where $B$ also occurs.
- **Biohazard | 误区**: Chronological order does not dictate conditioning. One can calculate $P(\text{past}|\text{future})$ just as easily as $P(\text{future}|\text{past})$.

<aside> 💡

**How to understand this? In this context, the “future” is settled?**

Conditioning is about information, not about time or causation.

Probability conditioning does **not** imply causal direction.

- $P(\text{future} \mid \text{past})$:
    
    If I know the past, how likely is the future?
    
- $P(\text{past} \mid \text{future})$:
    
    If I observe the future outcome, what does that tell me about the past?
    

</aside>

### 2.3 Bayes’ rule and the law of total probability

**Theorem 2.3.1 (Intersection of two events)**: $[ P(A \cap B) = P(B)P(A|B) = P(A)P(B|A) ]$

**Theorem 2.3.2 (Intersection of $n$ events | 链式法则)**: $[ P(A_1, A_2, \dots, A_n) = P(A_1)P(A_2|A_1)P(A_3|A_1, A_2) \dots P(A_n|A_1, \dots, A_{n-1}) ]$

**Theorem 2.3.3 (Bayes' Rule | 贝叶斯定理)**: $[ P(A|B) = \frac{P(B|A)P(A)}{P(B)} ]$

- **Bayes' Rule (Odds form)**: $[ \frac{P(A|B)}{P(A^c|B)} = \frac{P(A)}{P(A^c)} \cdot \frac{P(B|A)}{P(B|A^c)} ]$

**Theorem 2.3.6 (Law of Total Probability, LOTP | 全概率公式)**: Let $A_1, \dots, A_n$ be a partition of the sample space $S$. Then: $[ P(B) = \sum_{i=1}^n P(B|A_i)P(A_i) ]$

### 2.4 Conditional probabilities are probabilities

- **Metatheorem**: Any result valid for unconditional probabilities is also valid for conditional probabilities, provided all probabilities are conditioned on the same event $E$.
- **Properties under conditioning**:
    - $P(A^c|E) = 1 - P(A|E)$
    - $P(A \cup B|E) = P(A|E) + P(B|E) - P(A \cap B|E)$
- **Bayes' Rule with extra conditioning**: $[ P(A|B, E) = \frac{P(B|A, E)P(A|E)}{P(B|E)} ]$
- **LOTP with extra conditioning**: $[ P(B|E) = \sum_{i=1}^n P(B|A_i, E)P(A_i|E) ]$

### 2.5 Independence of events

**Definition 2.5.1 | 事件独立**: Two events $A$ and $B$ are independent if: $[ P(A \cap B) = P(A)P(B) ]$

- **Equivalent condition**: If $P(B) > 0$, then $A, B$ are independent if and only if $P(A|B) = P(A)$.
- **Conditional Independence | 条件独立**: $A$ and $B$ are conditionally independent given $E$ if: $[ P(A \cap B | E) = P(A|E)P(B|E) ]$
- **Important Distinction**:
    - Independence $\nRightarrow$ Conditional Independence.
    - Conditional Independence $\nRightarrow$ Independence.

### 2.6 Coherency of Bayes’ rule

- **Principle**: Sequential updating (updating on $B$, then on $C$) yields the same final probability as simultaneous updating (updating on $B \cap C$).

### 2.7 Conditioning as a problem-solving tool

- **Strategy 1: Condition on "what you wish you knew"**:
    - Use LOTP to break a hard problem into simpler cases.
    - Example: Monty Hall problem (condition on the car's location).
- **Strategy 2: First-step analysis**:
    - In recursive or multi-stage experiments, condition on the outcome of the first stage.
    - Example: Gambler's Ruin (condition on the first win/loss).

### 2.8 Pitfalls and paradoxes

- **Prosecutor's fallacy | 检察官谬误**: Confusing $P(A|B)$ with $P(B|A)$. Specifically, confusing the probability of the evidence given innocence with the probability of innocence given the evidence.
- **Defense attorney's fallacy**: Failing to condition on all available evidence (e.g., ignoring that a murder actually occurred).
- **Simpson’s paradox | 辛普森悖论**: A phenomenon where a trend appears in several groups of data but disappears or reverses when these groups are combined. This is often caused by a confounding variable.

### 2.10 R

- **Conditional Probability Simulation**: Approximate $P(A|B)$ using `nAB / nB` (counts of $A \cap B$ divided by counts of $B$) in a large number of repetitions.
- **Key Functions**:
    - `sample()`: Useful for simulating random experiments.
    - `sum(condition1 & condition2)`: Counts how often both conditions are met.