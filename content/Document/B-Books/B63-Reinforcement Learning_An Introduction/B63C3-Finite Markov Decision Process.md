---
tags:
  - Machine_Learning
  - Reinforcement_Learning
aliases:
---
[[KB1.1-Agent]] 
[[KB1.2-Reinforcement Learning]] 
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

### 3.2 Goals and Rewards

- **Reward Signal | 奖励信号**: A simple number $R_t$ sent from the environment to the agent.
- **Goal**: To maximize the total amount of reward (cumulative reward) received over the long run.
- **The Reward Hypothesis**: "That all of what we mean by goals and purposes can be well thought of as the maximization of the expected value of the cumulative sum of a received scalar signal (called reward)".
- **Note**: The reward signal is the way of communicating _what_ the agent is to achieve, not _how_ it is to achieve it.

### 3.3 Returns

- **Expected Return | 期望回报 ($G_t$)**: The specific function of the reward sequence that the agent seeks to maximize.
- **Simple Sum (Episodic Tasks)**:
    - $G_t = R_{t+1} + R_{t+2} + R_{t+3} + \dots + R_T$.
    - Used in **Episodic Tasks | 回合制任务**, where interaction breaks into subsequences (episodes) ending in a terminal state.
- **Discounted Return | 折扣回报**:
    - $G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \dots = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}$.
    - **Discount Rate | 折扣率 ($\gamma$)**: $0 \le \gamma \le 1$. It determines the present value of future rewards.
    - If $\gamma < 1$ and the reward sequence is bounded, the infinite sum has a finite value.

### 3.4 Unified Notation for Episodic and Continuing Tasks

- **Continuing Tasks | 连续性任务**: Tasks where the agent–environment interaction does not break naturally into episodes but continues without limit.
- **Unification**: Episode termination is treated as entering a special **absorbing state** that transitions only to itself and generates zero rewards.
- **Unified Return Formula**:
    - $G_t = \sum_{k=0}^{T-t-1} \gamma^k R_{t+k+1}$.
    - Allows for the possibility that $T = \infty$ or $\gamma = 1$ (but not both).

### 3.5 The Markov Property

- **Definition**: A state signal that compactly summarizes the past without degrading the ability to predict the future.
- **Requirement**: The state $S_t$ should include all information about the history of sensations that make a difference to the future.
- **Causal Dynamics**: In a Markov state, the environment's response at $t+1$ depends only on the state and action at $t$.
- **Significance**: decisions and values are assumed to be a function only of the current state; all theory in the book assumes Markov state signals.

### 3.6 Markov Decision Processes

- **MDP | 马尔可夫决策过程**: A reinforcement learning task that satisfies the Markov property.
- **Finite MDP**: An MDP with finite state, action, and reward sets.
- **Dynamics Function**:
    - $p(s', r|s, a) \doteq \text{Pr}{S_{t+1} = s', R_{t+1} = r | S_t = s, A_t = a}$.
    - This function completely specifies the dynamics of a finite MDP.
- **Derived Equations**:
    - **State-transition probabilities**: $p(s'|s, a) = \sum_{r \in \mathcal{R}} p(s', r|s, a)$.
    - **Expected rewards for state–action pairs**: $r(s, a) = \sum_{r \in \mathcal{R}} r \sum_{s' \in \mathcal{S}} p(s', r|s, a)$.
- **Transition Graph**: A summary of MDP dynamics where large open circles are states and small solid circles are state–action pairs.

### 3.7 Value Functions

- **Definition**: Functions of states (or state-action pairs) that estimate "how good" it is for an agent to be in a given state, measured by expected return.
- **State-value function ($v_\pi$)**:
    - $v_\pi(s) \doteq \mathbb{E}_\pi [G_t | S_t = s]$.
- **Action-value function ($q_\pi$)**:
    - $q_\pi(s, a) \doteq \mathbb{E}_\pi [G_t | S_t = s, A_t = a]$.
- **Bellman Equation for $v_\pi$**:
    - $v_\pi(s) = \sum_{a} \pi(a|s) \sum_{s', r} p(s', r|s, a) [r + \gamma v_\pi(s')]$.
    - It expresses a relationship between the value of a state and the values of its successor states.
- **Backup Diagrams | 回溯图**: Graphical summaries that transfer value information from successor states back to a current state or state-action pair.

### 3.8 Optimal Value Functions

- **Optimal Policy | 最优策略 ($\pi_*$)**: A policy that is better than or equal to all other policies ($\pi \ge \pi'$ if $v_\pi(s) \ge v_{\pi'}(s)$ for all $s$).
- **Optimal State-value Function ($v_*$)**:
    - $v_*(s) \doteq \max_\pi v_\pi(s)$.
- **Optimal Action-value Function ($q_*$)**:
    - $q_*(s, a) \doteq \max_\pi q_\pi(s, a)$.
- **Bellman Optimality Equation**:
    - For $v$_: $v_(s) = \max_{a \in \mathcal{A}(s)} \sum_{s', r} p(s', r|s, a) [r + \gamma v__(s')]$*.
    - For $q_: q_(s, a) = \sum_{s', r} p(s', r|s, a) [r + \gamma \max_{a'} q_*(s', a')]$.
- **Greedy Policy**: A policy that is greedy with respect to $v_*$ is an optimal policy.

### 3.9 Optimality and Approximation

- **Limitations**: Explicitly solving the Bellman optimality equation is rarely practical because:
    1. Accurate dynamics of the environment are often unknown.
    2. Computational resources are usually insufficient (e.g., Backgammon has $10^{20}$ states).
    3. The Markov property may not fully hold.
- **Tabular Case**: Small finite state sets where approximations can be stored in arrays or tables.
- **Approximation**: For large spaces, functions must be represented more compactly using parameterized functions.
- **RL Advantage**: RL can focus on frequently encountered states, potentially ignoring a large fraction of the state set that never occurs in practice.

### 3.10 Summary

- Reinforcement learning is about learning from interaction to achieve a goal.
- Key elements: **Actions** (choices), **States** (basis for choices), **Rewards** (basis for evaluation).
- **Return**: The function of future rewards to be maximized (undiscounted for episodic, discounted for continuing).
- **MDP**: An environment satisfying the Markov property with finite state/action sets.
- **Value Functions**: $v_\pi$ and $q_\pi$ satisfy recursive Bellman equations.
- **Optimality**: An ideal that agents approximate to varying degrees due to computational/memory limits.