# [[B63C3-Finite Markov Decision Process]]
### 3.1 The Agent–Environment Interface

- **Definitions**:
    - **Agent | 智能体**: The learner and decision-maker.
    - **Environment | 环境**: Everything outside the agent that it interacts with.
- **Interaction Process**:
    - The agent and environment interact at a sequence of discrete time steps, $t = 0, 1, 2, 3, \dots$.
    - At each step $t$, the agent receives a representation of the environment's **state** $S_t \in \mathcal{S}$ and selects an **action** $A_t \in \mathcal{A}(S_t)$.
    - One time step later, the agent receives a numerical **reward** $R_{t+1} \in \mathcal{R} \subset \mathbb{R}$ and finds itself in a new state $S_{t+1}$.
- **Policy | 策略 ($\pi_t$)**:
    - A mapping from states to probabilities of selecting each possible action.
    - $\pi_t(a|s)$: The probability that $A_t = a$ if $S_t = s$.
- **Boundary**: The boundary between agent and environment is drawn at the limit of the agent's control, not necessarily its physical body.